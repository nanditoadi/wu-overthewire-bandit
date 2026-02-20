# Bandit Level 19 → Level 20

## Level Goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

---

## Login
First, connect to the server using SSH:

```bash
ssh bandit19@bandit.labs.overthewire.org -p 2220
```

Password:
```
Password from previous level
```

---

## Solution Steps

### 1. List files in the home directory
```bash
ls
```

Explanation:  
This shows a binary file named `bandit20-do`.

---

### 2. Execute the setuid binary without arguments
```bash
./bandit20-do
```

Explanation:  
Running the binary without arguments displays usage instructions.  
It reveals that the program executes a command **as user bandit20**.

---

### 3. Use the binary to read the password file
```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

Explanation:
- `bandit20-do` is a **setuid binary**
- It runs with the permissions of user `bandit20`
- This allows access to `/etc/bandit_pass/bandit20`, which is normally restricted

---

### 4. Retrieve the password
The command outputs the password for the next level.

---

## Key Concept
This level introduces **setuid binaries**:
- A setuid program runs with the file owner’s privileges
- It can be used to execute commands as another user
- Misconfigured setuid binaries can lead to privilege escalation

---

## Commands Used
- `ls` : list directory contents
- `./binary` : execute a local program
- `cat` : display file contents
