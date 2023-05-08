# Lab Report 3 - Researching Commands

## Getting infomation using `grep` command

![image](https://user-images.githubusercontent.com/123513732/236664973-1cf199fe-f464-4d76-b3a8-be4801ebe399.png)

![image](https://user-images.githubusercontent.com/123513732/236664898-9e8c97a6-3ef0-486f-b9e8-0266030ab170.png)
Description: To find more infomration on how to use the `grep` coomand I used the `man grep` command which displays the manual page in the command prompt. Some of the sections of the manual include the name, a brief description of what it does, synopsis, an overview of the syntax, description, an explantation of how it works, and more.

## Ways to Use `grep`
![image](https://user-images.githubusercontent.com/123513732/236665407-f0a47518-4076-47c5-8c05-1f0a32292dcc.png)
Description: Although the `man grep` command was useful in finding information about the command in general I wanted to look for more interesting ways of using the features and even combining them. I used chatgpt to look up more ways to use the grep command:https://chat.openai.com/. The following uses of grep are taken from descriptions by chatgpt.

## Basic Search
`grep "search term" <file name>`
![image](https://user-images.githubusercontent.com/123513732/236665801-03d9142a-55ca-4d33-80ff-640ea2def2ed.png)
Description: The most basic way to search using grep is searching for a single word within a single file. To do so, we call the `grep` command followed by the term we are searching for in parenthesis, and lastly the file name. For this case I also needed to include the part of the path because I was still in the `stringsearch` directory.

`grep "acid" journal.pbio.0020035.txt`
![image](https://user-images.githubusercontent.com/123513732/236668434-09165f47-33e1-431e-99b0-5377864a3dcf.png)
Description: For this example I used `cd` to get into the `stringsearch-data` directory, then `technical` andy lastly `plos`. Since I am directly in the directory that contains the .txt file I do not need to provide a path and can use the basic search command similarly, this time I searched for "acid" as the search name. A note is that the basic search is case sensitive so it only returns lines where the search name is spell exactly as it is listed, so lines containing "Acid" would not be returned.

## Search multiple files
`grep "search term" <file1> <file2> <file3>`
![image](https://user-images.githubusercontent.com/123513732/236668809-58f708ee-a513-4fac-904a-c2cfb00f3b23.png)
Description: We can also search for a search term in multiple files by adding a space after each file. In this example I searched for the term "disease" in three dirrent files within the `plos` directory. The result that I get labels all the lines with the file name first before listing out the lines that match. This can be useful to find words across multiple files.

`grep "target" plos/journal.pbio.0020013.txt 911report/chapter-3.txt biomed/1471-2091-3-4.txt`
![image](https://user-images.githubusercontent.com/123513732/236669136-b6d4039d-38da-4310-90e2-82628c290e2a.png)
Description: For this example I chose three different files from three different directories, `plos`, `911report`, and `biomed`. This functions similarly to the previous example except the directory of each file is included since they aren't in the same directory. This way of using grep would be useful for searching words in file across different directories.

## Search for multiple words 
`grep "searchTerm1\|searchTerm2" <file name>`
![image](https://user-images.githubusercontent.com/123513732/236714141-f687aebd-ea2a-4a48-a5ba-8ce615a7f922.png)
Description: I had not idea that grep allowed for searching of multiple words until I asked ChatGpt. To search for more than one word within a file we need to include `\|` between the words we want to search which functions like an "OR" operator. For this case I wanted to search for "autoimmune" and "range" within a text file inside of the biomed directory which I also referenced in the path. This method of using grep can be useful to searching multiple words across files without having to call the search multiple times.

`grep "cells\|genes" plos/journal.pbio.0020040.txt biomed/ar118.txt`
![image](https://user-images.githubusercontent.com/123513732/236716054-8c1b47d3-71f2-49bf-80e7-7c4e6e4f24a4.png)
Description: In this example I combined the command's capability to search for multiple words and searching across multiple files. I searched for 

## Case-insensitive Search
`grep -i "search term" <file name>`
![image](https://user-images.githubusercontent.com/123513732/236669321-a4c6fa73-8d62-422a-bb0e-b0ec5e47f1f8.png)

`grep -i "search term" <file1> <file2>`
![image](https://user-images.githubusercontent.com/123513732/236669461-35cf46cd-bcc5-49a3-a2d6-11fec0612c9c.png)

## Inverse Match Search(printing all lines that do not match search term)
`grep -v "search name" <file name>`
![image](https://user-images.githubusercontent.com/123513732/236724580-b3b42dad-43ac-4f3a-a6ad-c477a038bba7.png)

`grep -v -i "the\|risk\|death" plos/pmed.0020180.txt`
![image](https://user-images.githubusercontent.com/123513732/236724940-b0877bb8-c36b-4213-9f44-2e5225c5d31e.png)

## Line Count with Grep
`grep -n "search name" <file name>`
![image](https://user-images.githubusercontent.com/123513732/236725272-d8172630-6acf-4d71-af8e-9a5133422fde.png)

`grep -v -i -n "the\|risk\|death" plos/pmed.0020180.txt`
![image](https://user-images.githubusercontent.com/123513732/236725348-0ae20c2f-6a04-4098-b0de-6cd96ae5c857.png)
