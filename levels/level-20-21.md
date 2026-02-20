# Bandit Level 20 → Level 21

## Level Goal
There is a **setuid binary** in the home directory.  
This binary will:
1. Connect to `localhost` on a port you specify as a command-line argument
2. Read one line of text from that connection
3. Compare it with the password from the previous level (**bandit20**)
4. If the password is correct, it will send back the password for the next level (**bandit21**)

---

## Login
First, connect to the server using SSH:

```bash
ssh bandit20@bandit.labs.overthewire.org -p 2220
```

Password:
```
Password from previous level
```

---

## Solution Steps

### 1. Check the home directory
```bash
ls -la
```

Output shows a file:
```
suconnect
```

Explanation:
- `suconnect` is a **setuid binary**
- It runs with higher privileges and connects to a local port

---

### 2. Start a listener using netcat
Open a new terminal or session and run:
```bash
nc -lvnp 1234
```

Explanation:
- `-l` : listen mode  
- `-v` : verbose  
- `-n` : numeric IP only  
- `-p` : specify port  

This terminal will wait for incoming connections.

---

### 3. Run the suconnect binary
Back in the `bandit20` terminal:
```bash
./suconnect 1234
```

Explanation:
- `suconnect` connects to `localhost:1234`
- It waits for input to verify the password

---

### 4. Send the bandit20 password
In the **netcat listener terminal**, type the password from bandit20:
```
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

If correct, the output will be:
```
Password matches, sending next password
```

Then it sends the password for the next level:
```
EeoULMCra2qad3gkY5i6lDXSTCpBuOBt
```

---

## Result
The password for **Bandit Level 21**.
---

## Key Concepts
- **Setuid binaries** run with elevated privileges
- Local **client-server communication**
- `netcat` is used to simulate a server
- Password verification happens over a network connection

---

## Commands Used
- `ls -la`
- `nc -lvnp 1234`
- `./suconnect 1234`
