# Bandit Level 12 → Level 13

## Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Login
```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

Password:
```
Password from previous level
```

---

## Solution Steps

### 1. Create a working directory
```bash
mkdir /tmp/solve
cp data.txt /tmp/solve
cd /tmp/solve
```

Explanation:  
We use `/tmp` because we need write permission to extract multiple files safely.

---

### 2. Convert hexdump back to binary
```bash
xxd -r data.txt data.out
```

Explanation:  
`xxd -r` reverses the hexdump into its original binary format.

---

### 3. Identify and extract repeatedly

Now use this pattern:

```bash
file data.out
```

Then extract according to the detected type:

- If **gzip**:
```bash
mv data.out data.gz
gzip -d data.gz
```

- If **bzip2**:
```bash
mv data.out data.bz2
bzip2 -d data.bz2
```

- If **tar archive**:
```bash
tar -xf data.out
```

After each extraction:
```bash
file <new_file>
```

Repeat the process until the file type becomes:

```
ASCII text
```

---

### 4. Read the final file
```bash
cat <final_file_name>
```

This reveals the password for the next level.

---

## Key Concept

The core of this level is:

- Use `file` to identify the compression type
- Extract according to the detected format
- Repeat until no compression layers remain

## Commands Used

- `mkdir /tmp/solve`  
  Create a working directory in `/tmp`.
- `cp data.txt /tmp/solve`  
  Copy the data file into the working directory.
- `cd /tmp/solve`  
  Change into the working directory.
- `xxd -r data.txt data.out`  
  Reverse the hexdump back into its original binary format.
- `file <filename>`  
  Identify the file type to determine the correct extraction method.
- `mv <oldname> <newname>`  
  Rename files to match the correct extension before decompression.
- `gzip -d <file.gz>`  
  Decompress gzip files.
- `bzip2 -d <file.bz2>`  
  Decompress bzip2 files.
- `tar -xf <file>`  
  Extract tar archive files.
- `cat <filename>`  
  Display the final ASCII text file containing the password.
