# Bandit Level 16 → Level 17

## Level Goal
The credentials for the next level can be retrieved by submitting the password of the current level to a port on `localhost` in the range `31000–32000`.

Only one server will return the correct credentials.  
Some ports use plain text, others use SSL/TLS.

---

## Login
First, connect to the server using SSH:

```bash
ssh bandit16@bandit.labs.overthewire.org -p 2220
```

Password:
```
Password from previous level
```


---

## Solution Steps

### 1. Scan open ports on localhost
```bash
nmap localhost -p 31000-32000
```

Explanation:  
This command scans ports `31000` to `32000` on localhost to find which ports are listening.

---

### 2. Identify the SSL/TLS-enabled service
From the scan results and trial, one port accepts SSL/TLS connections and returns a meaningful response.

In this case, the correct port is:
```
31790
```

---

### 3. Send the password using SSL/TLS
```bash
echo "<current_level_password>" | openssl s_client -quiet -connect localhost:31790
```

Explanation:
- `openssl s_client` is used to connect to SSL/TLS services
- `-quiet` hides certificate noise and keeps input/output clean
- The password is sent via `echo` and piped into the SSL connection

---

### 4. Receive SSH private key
If the password is correct, the server responds with:

```text
Correct!
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

This output is the **SSH private key** for the next level (`bandit17`).

---

### 5. Save the private key locally
Copy the key into a file (for example `sshkey17.private`) on your local machine and set proper permissions:

```bash
chmod 400 sshkey17.private
```

Explanation:  
SSH requires private keys to be readable only by the owner.

---

### 6. Log in to the next level
```bash
ssh bandit17@bandit.labs.overthewire.org -p 2220 -i sshkey17.private
```

This logs you in as `bandit17`.

---

## Key Concept
This level tests:
- Port scanning with `nmap`
- Differentiating plain TCP vs SSL/TLS services
- Using `openssl s_client` for encrypted communication
- Handling SSH key-based authentication

---

## Commands Used
- `nmap` : scan open ports on a host
- `echo` : send input to another command
- `openssl s_client` : connect to SSL/TLS services
- `chmod` : change file permissions
- `ssh -i` : log in using a private SSH key
