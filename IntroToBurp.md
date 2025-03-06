# picoCTF Challenge: "Intro to Burp"

## Introduction
This guide will help you solve the **"Intro to Burp"** challenge from picoCTF. It introduces the use of **Burp Suite**, a web security testing tool, to analyze and manipulate HTTP requests.

## Steps to Solve the Challenge

### Step 1: Open the Challenge Link
Click on the challenge-provided link and open it in **Burp Suite's** built-in browser.

### Step 2: Configure Burp Suite
1. Open **Burp Suite**.
2. Go to **Proxy** > **Intercept**.
3. Enable **Intercept responses** to capture both requests and responses.
4. Click **Open Browser** and enter the challenge URL.

### Step 3: Register an Account
1. On the registration page, enter random details (e.g., use "admin" for simplicity).
2. Click **Register**.
3. Burp Suite will capture a **CSRF token** and **Session ID**.
4. Forward all requests until reaching the **dashboard page**.

### Step 4: Bypassing One-Time Password (OTP)
1. The dashboard requests a **one-time password (OTP)**.
2. Enter a random value and submit.
3. Burp Suite will capture the request.
4. In Burp's **HTTP history**, find the OTP request.
5. **Remove the OTP variable** entirely.
6. Forward the modified request.

### Step 5: Retrieve the Flag
By removing the OTP check, the server assumes a successful login and grants access to the protected page containing the flag.

The flag will appear on the page:
```
picoCTF{#0TP_Bypvss_SuCc3$S_3e3ddc76}
```

### Step 6: Submit the Flag
Copy and submit the flag in the picoCTF challenge platform to complete the challenge. 🎉

---

## Summary
- Use **Burp Suite** to capture and modify HTTP requests.
- Remove the **OTP variable** in the request to bypass authentication.
- Successfully access the flag-protected page.

Happy hacking! 🚀
