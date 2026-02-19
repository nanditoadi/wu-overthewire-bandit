# Level 2 → Level 3

## Level Goal
The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

## Login
First, connect to the server using SSH:

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

Password:
```
Password from previous level
```

## Solution Steps
1. First, we try to read the file directly::
``` bash
cat ./--spaces in this filename--
```
Output: `No such file or directory`

Explanation: The command fails because the filename contains spaces.
In the shell, spaces are used to separate arguments, so the filename is split into multiple parts and cat treats them as different files.

2. To read the file correctly, we use quotes::
``` bash
cat ./"--spaces in this filename--"
```
This command displays the contents of the file, which is the password for the next level.

## Commands Used
- `cat`: view file contents
