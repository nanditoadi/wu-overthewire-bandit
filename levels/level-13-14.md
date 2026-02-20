# Bandit Level 13 → Level 14

## Level Goal
The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`.
Instead of a password, we are given a **private SSH key** that can be used to log in as `bandit14`.

## Login
Connect to the server using SSH:

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

Password:
```
Password from previous level
```

---

## Solution Steps

### 1. Locate the SSH private key
List the files in the home directory:

```bash
ls
```

You will find a file named:

```
sshkey.private
```

Explanation:  
This file is an SSH private key that allows authentication as `bandit14` without using a password.

---

### 2. Copy the private key to your local machine
From your local machine (outside the Bandit server), use `scp` to copy the key:

```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```

Explanation:
- `scp` is used to securely copy files over SSH
- `-P 2220` specifies the SSH port
- `.` means copy the file to the current local directory

---

### 3. Fix private key permissions
Set the correct permissions for the SSH key:

```bash
chmod 600 sshkey.private
```

Explanation:  
SSH refuses to use private keys that are accessible by other users.  
`600` ensures only the owner can read and write the key.

---

### 4. Log in as bandit14 using the private key
Use the key to log in:

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220 -i sshkey.private
```

Explanation:
- `-i sshkey.private` tells SSH to use the provided private key for authentication

---

### 5. Read the password for the next level
Once logged in as `bandit14`, run:

```bash
cat /etc/bandit_pass/bandit14
```

This command displays the password for **Bandit Level 14**.

---

## Key Concept

This level introduces **SSH key-based authentication**:
- Private keys can replace passwords
- File permissions are critical for SSH security
- Access is granted based on user identity, not file location

---

## Commands Used
- `ls` : list directory contents
- `scp` : securely copy files over SSH
- `chmod` : change file permissions
- `ssh` : connect to a remote server using SSH
- `cat` : display file contents
