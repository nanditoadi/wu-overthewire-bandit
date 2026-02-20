# Level 5 → Level 6

## Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

## Login
First, connect to the server using SSH:

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

Password:
``
Password from previous level
``

## Solution Steps
1. List the contents of the home directory. You will see a directory named `inhere`:
```bash
ls
```
2. Enter the `inhere` directory:
```bash
cd inhere
```
3. List all subdirectories:
```bash
ls -la
```
The directory contains multiple subdirectories named maybehere00 to maybehere19.

4. Search for a file that is exactly 1033 bytes in size:
```bash
find ./ -size 1033c
```
``
Output: ./maybehere07/.file2
``


5. Read the contents of the file:
```bash
cat ./maybehere07/.file2
```
This command displays the password for the next level.

## Commands Used
- `cat`: view file contents
- `ls` : list directory contents
- `cd` : change directory
- `find` : search for files based on conditions
