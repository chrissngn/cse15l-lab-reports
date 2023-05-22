# Lab Report 4 - VIM 

## Step 1 - Editing from command line using VIM

Log into ieng6 account:
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/b6b28c55-e094-49ba-89b6-4afe1273da50)

Clone repository using git:
```
$ git clone https://github.com/ucsd-cse15l-s23/lab7
```
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/3cd7d7e5-203f-4058-8763-4e0c1de5984b)

Cd into lab7 repository and run vim command on ListExamples.java(the file we are trying to edit):
```
$vim ListExamples.java
```
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/0fd296df-178d-4084-8cb9-812c21490321)

Edit file(use vim commands to navigate file and edit):
These are some of the commands I used,
`j` and `k` to move down and up, `h` and `l` to move left and right
`x` to delete character the cursor is hovering over
`i` key to insert
`esc` key to go back to normal mode
`:q` to quit
`:wq`to save and quit

Some of the edits I made, 
index1 to become index2
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/57531971-377d-4e55-861d-5f5348aeb77d)

change name of StringChecker from sc to checker
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/1a683445-2b9b-45dc-bf2e-0a2dbc2def3b)

## Step 2 - Generating SSH Keys for ieng6:
Run `ssh-keygen` command in local terminal,
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/4d3650de-cbf8-4540-99b9-6ebce8d3e802)

Click enter, type `y`, and hit `enter` key until randomart image appears,
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/28d4e98b-958a-449d-b06b-a94c449197bc)

Sign into ieng6 account, type in `mkdir .ssh`, and sign out,
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/b26c0ede-e15c-4e10-ba59-c84bf3798686)

Locate path to SSH Key enter in this format `scp <path to your public SSH key> cs15lsp23__@ieng6.ucsd.edu:~/.ssh/authorized_keys` and enter password for the last time,
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/45478fe2-8076-44af-ab69-be8dba442c44)

Re-log-onto ieng6 account to make sure that it doesn't ask for a password anymore,
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/1f1b3e12-35cc-478c-944c-003bbe086a9f)

## Step 3 - Generating SSH Keys for GitHub
Login into ieng6 account and run `ssh-keygen`,
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/877b9053-ddf7-4da5-91b2-81576f259a08)
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/18dea1c1-a840-41ef-9067-a32c0550bce5)

Display SSH public key using the `cat <path of your ssh key .pub file>`,
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/f811e221-a91f-4e66-8df5-c39cb3f78cbe)

Go to settings on GitHub, locate "Access" section, and select "SSH and GPG keys",
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/e38d7a3d-4402-48cd-996b-ce9d44d6bed0)

Create "New SSH key," select "Authentication key," and copy/paste SSH public key from command prompt,
![image](https://github.com/chrissngn/cse15l-lab-reports/assets/123513732/e1e5c410-70ee-4386-8f49-191050ca4bda)

## Step 4 - Base Line, editing and pushing repository

Some commands I used include,
Clone repository using `git clone <repo url>`

Cd into repo, `cd repo-name`

`git status` to see which files have been modified

`git add` to stage the changes you want to make

`git commit -m "descriptive message"` to commit staged changes

`git push` to push the commited changes or `git push -u origin <branch-name>` if it is the first time pushing changes

`git remote -v` to see the current remote URL being navigated

