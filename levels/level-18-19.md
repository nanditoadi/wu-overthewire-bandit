# Bandit Level 18 → Level 19

## Level Goal
The password for the next level is stored in a file called `readme` in the home directory.  
However, `.bashrc` has been modified to automatically log you out when you log in via SSH.

---

## Problem Analysis
Normally, logging in with SSH opens an interactive shell.  
In this level, `.bashrc` forces an immediate logout, so you **cannot stay logged in** to run commands manually.

---

## Solution Idea
SSH allows us to **execute a command directly during login**, without starting an interactive shell.  
This bypasses `.bashrc` and lets us read the file before being logged out.

---

## Solution Steps

### 1. Execute a command directly over SSH
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 ls
```

Explanation:  
- This command logs in and immediately runs `ls`
- `.bashrc` is bypassed because no interactive shell is started
- We can see that a file named `readme` exists

---

### 2. Read the password file directly
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat ./readme
```

Explanation:  
- `cat ./readme` is executed directly on login
- The password is printed before the forced logout occurs

---

### 3. Retrieve the password
The output of the command reveals the password for the next level.
---

## Key Concept
This level demonstrates that:
- `.bashrc` only affects **interactive shells**
- SSH can execute commands directly using:
  ```bash
  ssh user@host command
  ```
- Direct command execution can bypass restricted login environments

---

## Commands Used
- `ssh user@host command` : execute a command directly over SSH
- `ls` : list directory contents
- `cat` : display file contents
