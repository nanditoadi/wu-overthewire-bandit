# Level 8 → Level 9

## Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

## Login
First, connect to the server using SSH:

```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
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

2. Sort the contents of the file:
```bash
sort data.txt
```
Explanation:
The sort command arranges all lines in alphabetical order.
This step is required because the uniq command only works correctly on sorted input.

3. Find the line that appears only once:
``` bash
sort data.txt | uniq -u
```
Explanation:

- `uniq -u` displays only lines that occur exactly once
- `| (pipe)` passes the sorted output to uniq
The output of this command is the password for the next level.

## Commands Used
- `ls` : list directory contents
- `sort` : sort lines in a file
- `| (pipe)` : pass output from one command to another
- `uniq -u` : display unique (non-repeated) lines
