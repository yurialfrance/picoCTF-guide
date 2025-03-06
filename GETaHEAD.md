# picoCTF Challenge: "GET aHEAD"

## Introduction
This guide will help you solve the **"GET aHEAD"** challenge from picoCTF. This challenge involves inspecting HTTP headers to find a hidden flag.

## Challenge Description
**Author:** madStacks  
**Challenge URL:** [http://mercury.picoctf.net:15931/](http://mercury.picoctf.net:15931/)  
**Hint:** Maybe you have more than 2 choices. Check out tools like Burp Suite to modify your requests and look at the responses.

## Solution
### Step 1: Understanding HTTP Methods
When interacting with web servers, you can use different HTTP request methods:
- **GET**: Used to retrieve information from a server.
- **POST**: Used to send data to a server.
- **HEAD**: Similar to GET but only retrieves response headers (no body content).

For this challenge, we will use the **HEAD** method to check if any extra headers contain the flag.

### Step 2: Using `curl` to Send a HEAD Request
We use the following command:
```bash
curl -vv -I http://mercury.picoctf.net:15931/
```
#### Explanation of the Command:
- `curl` → Command-line tool for transferring data.
- `-vv` → Enables verbose output to see detailed request and response information.
- `-I` → Sends a **HEAD** request instead of a GET request (fetches only headers).

### Step 3: Analyzing the Response
The response from the server includes:
```bash
< HTTP/1.1 200 OK
< flag: picoCTF{r3j3ct_th3_du4l1ty_82880908}
< Content-type: text/html; charset=UTF-8
```
Here, we see that the flag is embedded in the HTTP response headers.

### Step 4: Submitting the Flag
The retrieved flag is:
```
picoCTF{r3j3ct_th3_du4l1ty_82880908}
```
Copy and submit it in the picoCTF challenge platform to complete the challenge. 🎉

---

## Summary
- Used the **HEAD** method with `curl -I` to retrieve HTTP headers.
- Found the flag inside the server's response headers.
- Successfully completed the challenge by submitting the flag.

Happy hacking! 🚀
