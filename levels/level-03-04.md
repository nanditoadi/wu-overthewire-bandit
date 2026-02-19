# Level 3 → Level 4

## Level Goal
The password for the next level is stored in a hidden file in the `inhere` directory.

## Login
First, connect to the server using SSH:

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
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
3. Show all files, including hidden ones:
```bash
ls -la
```
Explanation:
  - The -l option displays files in a long listing format with detailed information such as permissions, owner, and file size.
  - The -a option shows all files, including hidden files that start with a dot (.).


4. Identify the hidden file named `...Hiding-From-You`.
5. Read the contents of the file:
```bash
cat ...Hiding-From-You
```
This command displays the password for the next level.

## Commands Used
- `cat`: view file contents
- `ls` : list directory contents
- `cd` : change directory
