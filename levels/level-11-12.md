# Level 11 → Level 12

## Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Login
First, connect to the server using SSH:

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
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

2. View the contents of the file:
```bash
cat data.txt
```
Explanation:
The output looks like readable text but does not make sense. This is because the text is encoded using ROT13, a simple letter substitution cipher.

3. Decode the ROT13 encoded text:
``` bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
Explanation:
- cat data.txt reads the file content
- tr translates characters
- 'A-Za-z' represents all uppercase and lowercase letters
- 'N-ZA-Mn-za-m' shifts each letter by 13 positions (ROT13)
- | (pipe) passes the output from cat to tr
- The decoded output reveals the password for the next level.

## Commands Used
- `ls` : list directory contents
- `| (pipe)` : pass output from one command to another
- `cat` : display file contents
-`tr` : translate or substitute characters
