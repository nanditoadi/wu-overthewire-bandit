# Bandit Level 14 → Level 15

## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port `30000` on `localhost`.

## Access
Continue the SSH session from the previous level:

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220 -i sshkey.private
```

Explanation:  
Access to this level is done using SSH key authentication obtained from Level 13-14.

---

## Solution Steps

### 1. Connect to the local service on port 30000
```bash
nc localhost 30000
```

Explanation:  
This connects to a service running locally on port `30000` that expects input.

---

### 2. Submit the current level password
After the connection is established, enter the password from Level 13-14:

```
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

---

### 3. Retrieve the next password
The service responds with:

```
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

This value is the password for **Bandit Level 15**.

---

## Key Concept
This level demonstrates basic **client–server communication**:
- A service listens on a specific port
- Data is sent manually via `nc`
- Authentication is handled through simple text exchange

---

## Commands Used
- `ssh -i` : log in using a private SSH key
- `nc` : connect to a network service and send input
