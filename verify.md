# picoCTF: Verify Challenge Writeup

## Challenge Details
- **Title:** Verify
- **Author:** Jeffery John
- **Date:** 8/10/2024
- **Difficulty Level:** Easy
- **Platform:** [picoCTF](https://play.picoctf.org/practice/challenge/450)
- **Category:** Forensics

## Setup
This challenge can be solved using **Kali Linux** or any Linux-based system with OpenSSL installed.

## Challenge Description
We are given a set of files inside a directory. Our goal is to identify the correct file, decrypt it, and retrieve the flag.

## Step-by-Step Solution

### Step 1: List Files in the Home Directory
First, we list all files in the directory using:
```sh
ls -al
```
**Output:**
```
total 28
drwxr-xr-x 3 root root  4096 Mar 11 20:09 .
drwxr-xr-x 3 root root  4096 Aug 10 14:31 ..
-rw-r--r-- 1 root root    65 Mar 11 20:09 checksum.txt
-rwxr-xr-x 1 root root   856 Mar 11 20:09 decrypt.sh
drwxr-xr-x 2 root root 12288 Mar 11 20:09 files
```
Here, we see important files:
- `checksum.txt` (contains a hash value)
- `decrypt.sh` (a script used for decryption)
- `files/` directory (contains multiple files)

### Step 2: View the Hash in checksum.txt
We check the checksum.txt file:
```sh
cat checksum.txt
```
**Output:**
```
3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4
```

### Step 3: Find the Matching File
We need to find which file matches this hash using SHA256:
```sh
sha256sum files/* | grep "3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4"
```
**Output:**
```
3ad37ed6c5ab81d31e4c94ae611e0adf2e9e3e6bee55804ebc7f386283e366a4  files/e018b574
```
So, the correct file is **files/e018b574**.

### Step 4: Run the Decryption Script
We attempt to decrypt the file using the provided script:
```sh
./decrypt.sh files/e018b574
```
**Output:**
```
Error: 'files/e018b574' is not a valid file. Look inside the 'files' folder with 'ls -R'!
```
We got an error, meaning we need to analyze `decrypt.sh` to understand what it does.

### Step 5: Inspect decrypt.sh
We check the script using:
```sh
cat decrypt.sh
```
**Relevant Code:**
```sh
if ! openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "/home/ctf-player/drop-in/$file_name" -k picoCTF; then
    echo "Error: Failed to decrypt '$file_name'. This flag is fake! Keep looking!"
```
This means the script uses **OpenSSL AES-256-CBC decryption** with the password `picoCTF`.

### Step 6: Manually Decrypt the File
Since we now know the encryption method, we can manually run the OpenSSL command:
```sh
openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in "files/e018b574" -k picoCTF
```
**Output:**
```
picoCTF{trust_but_verify_e018b574}
```

### Step 7: Submit the Flag
The flag is:
```
picoCTF{trust_but_verify_e018b574}
```
Go back to the picoCTF website and submit the flag to complete the challenge! 🎉

---

## Lessons Learned
- **File Enumeration:** Using `ls -al` and `sha256sum` to analyze files.
- **Hash Matching:** Identifying a file by checking its SHA-256 checksum.
- **Script Analysis:** Understanding how decryption scripts work.
- **OpenSSL Decryption:** Manually decrypting files using OpenSSL commands.

This was an **easy** challenge but a great way to learn about file integrity verification and OpenSSL encryption! 🚀

