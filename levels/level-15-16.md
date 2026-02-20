# Bandit Level 15 → Level 16

## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port `30001` on `localhost` using SSL/TLS encryption.

---

## Login
First, connect to the server using SSH:

```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220
```

Password:
```
Password from previous level
```


---

## Solution Steps

### 1. Connect to port 30001 using SSL/TLS
```bash
openssl s_client -connect localhost:30001
```

Explanation:  
- `openssl s_client` is used to connect to a server using SSL/TLS.
- `-connect localhost:30001` specifies the local service and port.
- Unlike the previous level (`nc`), this service requires encrypted communication.

After running the command, you will see SSL handshake information and a `CONNECTED` message.

---

### 2. Submit the current level password
Once the connection is established, paste the password from Level 15-16 and press Enter:

```
<current_level_password>
```

---

### 3. Receive the next password
If the password is correct, the server responds with the password for **Bandit Level 16-17**.

---

## Helpful Note (About DONE / RENEGOTIATING / KEYUPDATE)

If you see messages like:

```
DONE
RENEGOTIATING
KEYUPDATE
```

This is normal behavior in SSL/TLS connections.  
The important part is that the connection remains open so you can send the password after `CONNECTED`.

---

## Key Concept

This level introduces:

- SSL/TLS encrypted communication
- The difference between plain TCP (`nc`) and encrypted connections (`openssl s_client`)
- Basic understanding of SSL handshake behavior

---

## Commands Used
- `openssl s_client` : connect to a server using SSL/TLS
- `ssh` : remote login
