# Level 10 → Level 11

## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data.

## Login
First, connect to the server using SSH:

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
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
The output is not readable because the content is encoded using Base64.

3. Decode the Base64 encoded data:
``` bash
cat data.txt | base64 --decode
```
Explanation:
- cat data.txt reads the file content
- base64 --decode decodes Base64 encoded text
- | (pipe) sends the output of cat to the decoder
- The decoded output reveals the password for the next level.

## Commands Used
- `ls` : list directory contents
- `| (pipe)` : pass output from one command to another
- `cat` : display file contents
- `base64 --decode` : decode Base64 encoded data
