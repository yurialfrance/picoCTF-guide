# Scavenger Hunt - picoCTF Challenge Guide

## Challenge Description
**Author:** picoCTF Team  
**Description:** There is some interesting information hidden around this site.

**Challenge URL:** [http://mercury.picoctf.net:39491/](http://mercury.picoctf.net:39491/)

**Hint:** You should have enough hints to find the files, don’t run a brute forcer.

---

## Step-by-Step Solution

### Step 1: Viewing the Page Source
Since the description hints that there is information hidden on the site, the first thing we should do is **view the page source**.

- Right-click on the webpage and select **View Page Source** (or press `Ctrl + U` on Windows / `Cmd + Option + U` on Mac).
- Look through the HTML code, and in **line 31**, we find the first part of the flag:
  
  ```html
  <!-- Here’s the first part of the flag: picoCTF{t -->
  ```

### Step 2: Checking the CSS File
- Go back to the webpage and locate the CSS file (`mycss.css`).
- Click on the CSS file to open it.
- Scroll to the bottom, and you’ll find the second part of the flag inside a comment:
  
  ```css
  /* CSS makes the page look nice, and yes, it also has part of the flag. Here’s part 2: h4ts_4_l0 */
  ```

### Step 3: Checking the JavaScript File
- Open the JavaScript file (`myjs.js`), but it doesn’t contain the flag.
- However, there is an important hint:
  
  ```js
  /* How can I keep Google from indexing my website? */
  ```
- This suggests checking the `robots.txt` file.

### Step 4: Checking robots.txt
- Open `robots.txt` by visiting:
  
  ```
  http://mercury.picoctf.net:39491/robots.txt
  ```
  
- The file contains another part of the flag:
  
  ```
  User-agent: *
  Disallow: /
  # Here’s part 3: t_0f_pl4c
  ```

### Step 5: Checking .htaccess
- Another hint in `robots.txt` suggests this is an Apache server.
- Apache servers sometimes use `.htaccess` for access control.
- Visit:
  
  ```
  http://mercury.picoctf.net:39491/.htaccess
  ```
  
- The file contains another flag piece:
  
  ```
  # Here’s part 4: 3s_2_lO0k
  ```

### Step 6: Checking .DS_Store (MacOS Metadata File)
- Another hint in `.htaccess` refers to "Store," which relates to `.DS_Store`, a hidden macOS file.
- Visit:
  
  ```
  http://mercury.picoctf.net:39491/.DS_Store
  ```
  
- This file contains the last part of the flag:
  
  ```
  # Here’s part 5: _f7ce8828}
  ```

### Step 7: Submitting the Flag
After gathering all parts, the final flag is:

```
picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_f7ce8828}
```

- Copy and submit it to picoCTF to earn **50 points**!

---

## Summary
This challenge teaches **basic web reconnaissance techniques**, such as:
- Viewing page source to find hidden comments.
- Checking CSS and JavaScript files for hints.
- Exploring `robots.txt` to discover hidden paths.
- Understanding Apache `.htaccess` and macOS `.DS_Store` files.

🔹 **Lesson learned:** Always check web files and metadata for hidden information in CTF challenges!

**Happy hacking!** 🏆
