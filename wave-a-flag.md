# picoCTF Challenge: "Wave a Flag"

## Introduction
This guide will walk you through solving the **"wave a flag"** challenge from picoCTF. It's a beginner-friendly challenge that introduces basic Linux command-line operations.

## Steps to Solve the Challenge

### Step 1: Download the Challenge File
The challenge provides a file named `warm`. Use `wget` to download it:
```bash
wget https://mercury.picoctf.net/static/a00f554b16385d9970dae424f66ee1ab/warm
```

### Step 2: Try Running the File
After downloading, check if the file is executable by attempting to run it:
```bash
./warm
```
If you see an error like:
```
zsh: permission denied: ./warm
```
this means the file does not have execute permissions.

### Step 3: Check File Permissions
List the files in the directory to see the current permissions:
```bash
ls -l
```
You should see something like this:
```
-rw-rw-r-- 1 user user 10936 Mar 15  2021 warm
```
The `-rw-rw-r--` indicates that the file is **not executable**.

### Step 4: Grant Execute Permissions
To make the file executable, run:
```bash
chmod +x warm
```
Now, verify by running:
```bash
ls -l
```
You should see the permission change to:
```
-rwxrwxr-x 1 user user 10936 Mar 15  2021 warm
```

### Step 5: Execute the File
Now that the file is executable, run it again:
```bash
./warm
```
It will output:
```
Hello user! Pass me a -h to learn what I can do!
```

### Step 6: Get the Flag
The hint suggests using `-h`, so run:
```bash
./warm -h
```
This will output:
```
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_********}
```

### Step 7: Submit the Flag
Copy the flag and submit it on the picoCTF platform. 🎉 Congratulations, you've solved the challenge!

## Summary
- Download the challenge file using `wget`.
- Check file permissions with `ls -l`.
- Grant execute permissions using `chmod +x`.
- Run the file and use `-h` to reveal the flag.
- Submit the flag to complete the challenge.

Happy hacking! 🚀
