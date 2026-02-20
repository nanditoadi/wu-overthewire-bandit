# Level 7 → Level 8

## Level Goal
The password for the next level is stored in the file data.txt next to the word millionth

## Login
First, connect to the server using SSH:

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

Password:
``
Password from previous level
``

## Solution Steps
1. List the contents of the home directory:
```bash
ls 
```
Explanation:
This command shows the files in the current directory. We can see a file named data.txt, which likely contains the password.

2. Try to display the contents of data.txt:
```bash
cat data.txt
```
Explanation:
This command outputs the entire content of the file.
However, data.txt is very large, so the output scrolls quickly and is difficult to read.

3. Filter the content to find the line containing the word millionth:
``` bash
cat data.txt | grep 'millionth'
```
Explanation:

- cat data.txt outputs the contents of the file
-| (pipe) sends the output to another command
- grep 'millionth' searches for lines containing the word millionth

This command returns only the line that contains millionth, and the password is located next to it.

## Commands Used
- `ls` : list directory contents
- `cat` : display file contents
- `grep` : search for specific text in output
- `| (pipe)` : pass output from one command to another
