# Level 1 → Level 2

## Level Goal
The password for the next level is stored in a file called - located in the home directory (`~`)

## Login
First, connect to the server using SSH:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

Password:
```
Password from previous level
```

## Solution Steps
1. To see view file contents of the file named `-`, we first try use cat:
``` bash
cat -
```
2. The command not work as expected, because `-` is interpreted as standard input (stdin)
3. To read the file literally named -, we must specify the path:
``` bash
cat ./-
```
Explanation: 
Using ./- tells the shell to look for a file named `-` in the current directory, where `.` represents the current directory.

## Commands Used
- `cat`: view file contents
