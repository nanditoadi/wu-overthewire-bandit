# Bandit Level 17 → Level 18

## Level Goal
There are two files in the home directory: `passwords.old` and `passwords.new`.  
The password for the next level is stored in `passwords.new` and is the **only line that has changed** compared to `passwords.old`.

---

## Access
Continue from the previous level (already logged in as `bandit17`.

---

## Solution Steps

### 1. List files in the home directory
```bash
ls
```

Explanation:  
This confirms the presence of the two files that need to be compared.

---

### 2. Compare the two password files
```bash
diff passwords.new passwords.old
```

Explanation:  
- `diff` compares two files line by line
- It shows the differences between them
- The output format indicates which line was changed

Example output:
```text
42c42
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> BMIOFKM7CRSLI97voLp3TD80NAq5exxk
```

- `<` indicates the line from `passwords.new`
- `>` indicates the line from `passwords.old`

---

### 3. Identify the correct password
The password for the next level is the line **from `passwords.new`**, which is:

```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

---

## Key Concept
This level introduces **file comparison**:
- `diff` helps identify changes between files
- Symbols `<` and `>` show which file the line comes from
- Only the modified line matters

---

## Commands Used
- `ls` : list directory contents
- `diff` : compare files line by line
