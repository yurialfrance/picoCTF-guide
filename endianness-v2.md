# Endianness-v2 picoCTF Writeup

## Challenge Information
**Challenge Name:** Endianness-v2  
**Author:** Junias Bonou  
**Category:** Forensics  
**Difficulty:** Medium

## Description
Here's a file that was recovered from a 32-bit system that organized the bytes in a weird way. We're not even sure what type of file it is. Download it [here](https://artifacts.picoctf.net/c_titan/114/challengefile) and see what you can get out of it.

## Solution

### Step 1: Download and Inspect the File
First, download the challenge file:
```bash
wget https://artifacts.picoctf.net/c_titan/114/challengefile -O challengefile
```

Check the file's signature:
```bash
file challengefile
```
It may not return meaningful results, so let's check the file in a hex editor.

### Step 2: Check File Signature in a Hex Editor
Use an online hex editor like [hexed.it](https://hexed.it/) or check manually using:
```bash
xxd challengefile | head -n 20
```
From the hex output, we see that the file signature resembles a JPEG file but appears reversed due to incorrect endianness.

### Step 3: Convert Little Endian to Big Endian
To fix the file format, we need to reorder the bytes from little-endian to big-endian. We can use the following Python script:

```python
import struct

def convert_little_to_big_endian(input_file_path, output_file_path):
    # Read the little-endian binary file
    with open(input_file_path, 'rb') as input_file:
        little_endian_data = input_file.read()

    # Convert the data to big-endian order
    # Assuming the data consists of 32-bit integers for this example
    # You can adjust the struct format string for different data types or sizes
    num_elements = len(little_endian_data) // 4  # Number of 32-bit integers
    big_endian_data = bytearray()

    for i in range(num_elements):
        little_endian_chunk = little_endian_data[i * 4:(i + 1) * 4]
        
        # Unpack little-endian and pack it again as big-endian
        value = struct.unpack('<I', little_endian_chunk)[0]
        big_endian_chunk = struct.pack('>I', value)
        
        big_endian_data.extend(big_endian_chunk)

    # Write the big-endian data to the output file
    with open(output_file_path, 'wb') as output_file:
        output_file.write(big_endian_data)

    print(f"Conversion complete. Output saved to {output_file_path}")

# Example usage
input_file_path = 'input_file_path'
output_file_path = 'output_big_endian.jpg'
convert_little_to_big_endian(input_file_path, output_file_path)

```

### Step 4: Rename and Open the File
Run the script:
```bash
python3 endian_converter.py
```
Rename the output file if necessary:
```bash
mv output_big_endian.jpg flag.jpg
```
Now, open the image:
```bash
eog flag.jpg  # Linux image viewer
```
The flag will be displayed in the image!

## Flag
```
picoCTF{certified_endianness}
```

## Lessons Learned
- File signatures and magic bytes help identify unknown files.
- Endianness affects how bytes are stored and interpreted.
- Python's `struct` module is useful for manipulating binary files.

---
This guide is designed for beginners with clear, step-by-step instructions. Happy hacking! 🎯
