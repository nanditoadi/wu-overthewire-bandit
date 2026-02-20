# Level 9 → Level 10

## Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Login
First, connect to the server using SSH:

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
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
This command shows the available files. The file data.txt is the target file.

2. Extract human-readable strings from the file:
```bash
strings data.txt
```
Explanation:
The strings command extracts printable, human-readable text from a binary file.
Since data.txt contains mostly binary data, this helps isolate readable strings.

3. Filter the strings that contain `=` characters:
``` bash
strings data.txt | grep '='
```
Explanation:
- grep '=' searches for lines containing the = character
- The pipe (|) passes the output of strings to grep
- The line preceded by several = characters contains the password for the next level.

## Commands Used
- `ls` : list directory contents
- `strings` : extract human-readable strings from binary files
- `| (pipe)` : pass output from one command to another
- `grep` : search for specific patterns
