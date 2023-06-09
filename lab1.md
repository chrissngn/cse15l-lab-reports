# Lab Report 1 - Remote Access and FileSystem - How to log into course specific account

## Step 1 - Access VS Code
Open or [install](https://code.visualstudio.com/download) vs code on your device. Depending on your device the layout may vary.

![Screenshot](vscodeOpen.png)

## Step 2 - Connect to Remote Server

If you are on Windows install git for [Windows](https://gitforwindows.org/).

After you have installed git on to your device you will need to access the git bash terminal on VSCode. To do this **Ctrl + `** to open the terminal, locate the **+** next to the powershell button, click on the down turned arrow, and select **Git Bash**.

![Screenshot](vscodeBash.png)

Once the Bash terminal is open you may now use ssh. In the terminal type in ssh followed by your course specific account user. For example:

```
$ ssh cs15lsp23ko@ieng6.ucsd.edu
```
If it is the first time you are logging on you might encounter this prompt:
```
⤇ ssh cs15lsp23ko@ieng6.ucsd.edu
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```
Type in **yes**. The prompt will then ask you to enter your password, enter your password.
```
⤇ ssh cs15lsp23ko@ieng6.ucsd.edu
The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
Password: 
```
We have some issues with ITS so after logging in you may encounter this prompt:
```
Connection closed by 128.54.70.238 port 22
```
If you are encountering this issue, try signing into your personal UCSD account followed by @ieng6.ucsd.edu:
```
⤇ ssh chn029@ieng6.ucsd.edu
```
Another option would be to sign in with your lab log in follow by -201 -202 or -203:
```
⤇ ssh cs15lsp23ko-202@ieng6.ucsd.edu
```
You will then see a prompt similar to this:
```
Last login: Thu Apr  6 14:30:58 2023 from its-cseb260-20.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   17:35:01   12  1.05,  1.12,  1.20
ieng6-202   17:35:01   7   4.23,  4.20,  4.26
ieng6-203   17:35:01   16  1.51,  1.50,  1.49
```
## Step 3 - Run Commands
Once you are logged in you are ready to run some commands, **cd**, **ls**, **pwd**, **mkdir**, and **cp**. For example:

`cd ~`
`cd`
`ls -lat`
`ls -a`
`ls <directory>` where <directory> is /home/linux/ieng6/cs15lsp23/cs15lsp23abc, where the abc is one of the other group members’ username
`cp /home/linux/ieng6/cs15lsp23/public/hello.txt ~/`
`cat /home/linux/ieng6/cs15lsp23/public/hello.txt`

![Screenshot](vscodeCommands.png)

The command `pwd` ran in the image stands for "print working directory" and after running the command the terminal returned "/home/linux/ieng6/oce/47/chn029" with is the current working directory. The next command being used is called `ls` which stand for "list" and to use this command we can call `ls <path>` which then lists out files and folders as displayed in the screenshot. `cp` is a command used to copy files or directories, however, since the file I was trying to copy did not exist it displays a message that says "no such file or directory." The `cat` or "concatenate" can be used to print the contents of the file by giving a path in the format of `cat <path> <another path>`.
