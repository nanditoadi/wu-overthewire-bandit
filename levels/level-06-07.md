# Level 6 → Level 7

## Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

## Login
First, connect to the server using SSH:

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

Password:
``
Password from previous level
``

## Solution Steps
1. List the contents of the home directory:
```bash
ls -la
```
Explanation:
The home directory does not contain the password file directly, so we need to search the entire filesystem.

2. Use the find command to search for the file with specific properties:
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

Explanation:

- / → start searching from the root directory (entire filesystem)

- user bandit7 → file must be owned by user bandit7

- group bandit6 → file must belong to group bandit6

- size 33c → file size must be exactly 33 bytes (c means bytes)

- 2>/dev/null → suppress permission denied errors to keep output clean
The directory contains multiple subdirectories named maybehere00 to maybehere19.
- **About `2>/dev/null`:**  
`2` represents **stderr (error messages)**.  
`/dev/null` is a special file that discards all data written to it.  

So, `2>/dev/null` redirects error messages to `/dev/null`, preventing permission denied errors from cluttering the output.

3. Identify the result:
``
/var/lib/dpkg/info/bandit7.password
``
This file matches all required conditions.

4. Read the contents of the file:
```bash
cat /var/lib/dpkg/info/bandit7.password
```
This command displays the password for the next level.

## Commands Used
- `ls` : list directory contents  
- `find` : search for files based on specific conditions  
- `-user` : match files owned by a specific user  
- `-group` : match files owned by a specific group  
- `-size` : match files with an exact size  
- `cat` : display file contents
