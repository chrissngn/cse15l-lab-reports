# Lab Report 2 - Servers and Bugs

## Part 1 - Create a Web Server

**Code for the Web Server - Server.java**
```
import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URI;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

interface URLHandler {
    String handleRequest(URI url);
}

class ServerHttpHandler implements HttpHandler {
    URLHandler handler;
    ServerHttpHandler(URLHandler handler) {
      this.handler = handler;
    }
    public void handle(final HttpExchange exchange) throws IOException {
        // form return body after being handled by program
        try {
            String ret = handler.handleRequest(exchange.getRequestURI());
            // form the return string and write it on the browser
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
        } catch(Exception e) {
            String response = e.toString();
            exchange.sendResponseHeaders(500, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}
public class Server {
    public static void start(int port, URLHandler handler) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);

        //create request entrypoint
        server.createContext("/", new ServerHttpHandler(handler));

        //start the server
        server.start();
        System.out.println("Server Started! Visit http://localhost:" + port + " to visit.");
    }
}

```
**Code for the Web Server - StringServer.java**
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String message = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format(message);
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    message += "\n" +parameters[1];
                    return String.format(message);
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

**Web Server in Action**
![Screenshot](StringServerBlank.png)
Description: In this screenshot the web server is launched with just the link which runs the handle and start methods in the Server.java file. Since the url was created the if statement in the main method did not run since 3000 is a valid port number. With the way I wrote this program the first if statement in the handle request method does get run which returns the `message` however it is blank since the default variable `message` is set to an empty string.

![Screenshot](StringServer1.png)
Description: 

![Screenshot](StringServer2.png)

To run this program compile using
`javac Server.java StringServer.java`

Then `java StringServer <any number between 1024 and 49151>`

Which returns a prompt in the terminal similar to this:
`Server Started! Visit http://localhost:3000 to visit.`

Every time the site is refreshed or a new command is added in the url the terminal returns the path `Path: /favicon.ico`for just a refresh and `Path: /add-message`when the command is used
![image](https://user-images.githubusercontent.com/123513732/233822684-7973e410-29a3-471f-b9bb-e87163c376ca.png)


