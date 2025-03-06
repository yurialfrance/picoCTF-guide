# picoCTF Challenge: "Nice netcat..."

## Introduction
This guide will help you solve the **"Nice netcat..."** challenge from picoCTF. It introduces the use of `netcat (nc)`, a command-line networking tool, and ASCII decoding.

## Steps to Solve the Challenge

### Step 1: Connect to the Server
The challenge provides a server address and port. Use `nc` (netcat) to connect:
```bash
nc mercury.picoctf.net 7449
```

### Step 2: Receive the Encoded Data
Upon connecting, you will receive a series of numbers:
```
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
102 
50 
100 
55 
99 
97 
102 
97 
125 
10
```
These numbers represent ASCII character codes in decimal format.

### Step 3: Convert Decimal to ASCII
To decode the message, go to [RapidTables ASCII Converter](https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html).

1. Copy the numbers.
2. Paste them into the "Decimal (bytes)" field.
3. Convert to ASCII.

The output will be:
```
picoCTF{g00d_k1tty!_n1c3_k1tty!_f2d7cafa}
```

### Step 4: Submit the Flag
Copy and submit the decoded flag to complete the challenge. 🎉

---

## Summary
- Use `nc` to connect to the provided server and port.
- Receive a series of decimal numbers representing ASCII codes.
- Convert the decimal values to ASCII text using [RapidTables](https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html).
- Submit the decoded flag.

Happy hacking! 🚀
