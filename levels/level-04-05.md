# Level 4 → Level 5

## Level Goal
The password for the next level is stored in the only human-readable file in the `inhere` directory. Tip: if your terminal is messed up, try the “reset” command.

## Login
First, connect to the server using SSH:

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
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
3. List all files in the directory:
```bash
ls 
```
4. Check the type of each file to find the human-readable one:
```bash
file ./*
```

Output:
- ./-file00: data
- ./-file01: OpenPGP Public Key
- ./-file02: OpenPGP Public Key
- ./-file03: data
-./-file04: data
- ./-file05: data
- ./-file06: data
- ./-file07: ASCII text
- ./-file08: data
- ./-file09: data


Explanation:
The `file` command identifies the file type.
`-file07` is the only file marked as `ASCII text`, which means it is human-readable.

5. Read the human-readable file:
```bash
cat ./-file07
```
This command displays the password for the next level.

## Commands Used
- `cat`: view file contents
- `ls` : list directory contents
- `cd` : change directory
- `file` : determine file type
