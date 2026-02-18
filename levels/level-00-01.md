# Level 0 → Level 1

## Level Goal
The password for the next level is stored in a file called `readme` located in the home directory. Use this password to log into `bandit1` using SSH. Whenever you find a password for a level, use SSH (on port `2220`) to log into that level and continue the game.

## Login
First, connect to the server using SSH:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Password:
```
bandit0
```

## Solution Steps
1. After logging in as `bandit0`, you are placed in the home directory (`~`).
2. List the files in the directory:
   ```bash
   ls
   ```
3. A file named `readme` appears.
4. View the contents of the file using:
   ```bash
   cat readme
   ```
5. The output of this command displays the password for **Level 1**.

## Commands Used
- `ssh`: connect to a remote server  
- `ls`: list files in a directory  
- `cat`: view file contents
