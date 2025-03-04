# picoCTF Challenge: "Information"

## Introduction
This guide will help you solve the **"Information"** challenge from picoCTF. It introduces you to extracting hidden metadata from files and decoding base64-encoded data.

## Steps to Solve the Challenge

### (Using Web Tools)

#### Step 1: Download the Image File
Use `wget` to download the provided image file:
```bash
wget https://mercury.picoctf.net/static/c28a959c5605d5f67480d5dd3a77f302/cat.jpg
```

#### Step 2: Check the Image for Hidden Data
Since the flag is not visible in the image, we should check if it is hidden inside the file's metadata.

Go to [Metadata2Go](https://www.metadata2go.com) and upload `cat.jpg` to analyze its metadata.

#### Step 3: Extract the Encoded Flag
From the metadata, look for a field containing an encoded string such as:
```
cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
```
This is a **Base64-encoded string** that likely contains the flag.

#### Step 4: Decode the Base64 String
Visit [Base64 Decode](https://www.base64decode.org/) and paste the extracted string to decode it.

You will get the flag in the format:
```
picoCTF{the_m3tadata_1s_modified}
```

#### Step 5: Submit the Flag
Copy and submit the decoded flag to complete the challenge. 🎉

---

## How to Embed Data in an Image (Using Kali Linux)
If you want to embed a secret file inside an image using **steghide**, follow these steps:

#### Step 1: Embed a Secret File
Run the following command to embed `my_secret_file.txt` inside an image:
```bash
steghide -ef my_secret_file.txt -cf cat_astro.jpg -sf suspicious_cat.jpg
```

#### Step 2: Set a Passphrase
You will be prompted to enter a passphrase:
```
Enter passphrase:
Re-Enter passphrase:
```

#### Step 3: Completed Stego File
After embedding, you will see:
```
embedding "my_secret_file.txt" in "cat_astro.jpg"... done
writing stego file "suspicious_cat.jpg"... done
```
Now, `suspicious_cat.jpg` contains the hidden data.

---

## Summary
- Download the image file using `wget`.
- Check the file’s metadata using [Metadata2Go](https://www.metadata2go.com).
- Extract the encoded flag and decode it with [Base64 Decode](https://www.base64decode.org/).
- Submit the flag to complete the challenge.
- (Bonus) Use `steghide` in Kali Linux to embed hidden data inside images.

Happy hacking! 🚀

