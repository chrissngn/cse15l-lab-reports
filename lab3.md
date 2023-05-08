# Lab Report 3 - Researching Commands

## Getting infomation using `grep` command

![image](https://user-images.githubusercontent.com/123513732/236664973-1cf199fe-f464-4d76-b3a8-be4801ebe399.png)
Description: The `man grep` command

![image](https://user-images.githubusercontent.com/123513732/236664898-9e8c97a6-3ef0-486f-b9e8-0266030ab170.png)

## Ways to Use `grep`
![image](https://user-images.githubusercontent.com/123513732/236665407-f0a47518-4076-47c5-8c05-1f0a32292dcc.png)
Description: I used chatgpt to look up ways to use the grep command, the following uses of grep are taken from descriptions by chatgpt.

## Basic Search
`grep "search term" <file name>`
![image](https://user-images.githubusercontent.com/123513732/236665801-03d9142a-55ca-4d33-80ff-640ea2def2ed.png)

`grep "acid" journal.pbio.0020035.txt`
![image](https://user-images.githubusercontent.com/123513732/236668434-09165f47-33e1-431e-99b0-5377864a3dcf.png)

## Search multiple files
`grep "search term" <file1> <file2> <file3>`
![image](https://user-images.githubusercontent.com/123513732/236668809-58f708ee-a513-4fac-904a-c2cfb00f3b23.png)

`grep "target" plos/journal.pbio.0020013.txt 911report/chapter-3.txt biomed/1471-2091-3-4.txt`
![image](https://user-images.githubusercontent.com/123513732/236669136-b6d4039d-38da-4310-90e2-82628c290e2a.png)

## Search for multiple words 
`grep "searchTerm1\|searchTerm2" <file name>`
![image](https://user-images.githubusercontent.com/123513732/236714141-f687aebd-ea2a-4a48-a5ba-8ce615a7f922.png)

`grep "cells\|genes" plos/journal.pbio.0020040.txt biomed/ar118.txt`
![image](https://user-images.githubusercontent.com/123513732/236716054-8c1b47d3-71f2-49bf-80e7-7c4e6e4f24a4.png)

## Case-insensitive Search
`grep -i "search term" <file name>`
![image](https://user-images.githubusercontent.com/123513732/236669321-a4c6fa73-8d62-422a-bb0e-b0ec5e47f1f8.png)

`grep -i "search term" <file1> <file2>`
![image](https://user-images.githubusercontent.com/123513732/236669461-35cf46cd-bcc5-49a3-a2d6-11fec0612c9c.png)

## Inverse Match Search(printing all lines that do not match search term)
`grep -v`
## Line Count with Grep
