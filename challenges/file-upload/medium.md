📤 File Upload – Medium Security Level

### 🛠️ Objective:
Bypass a simple content-type check to upload a PHP shell.

---

### 🔍 Observations

- Uploading a `.php` file directly returns an error.
- Source code shows a check on the **MIME type** (`uploaded_type`), expecting an image type like `image/jpeg` or `image/png`.

---

### 🧭 Exploitation Steps with Burp Suite

1. Intercept the file upload request using **Burp Suite**.
2. Locate the `Content-Type` header (e.g., `application/x-php`) and change it to:
````

Content-Type: image/png

````

3. Forward the modified request.

✅ The server will accept the file, bypassing the type check.

4. Start a Netcat listener:
```bash
nc -lnvp 1234
````

5. Visit the uploaded shell path in the browser to trigger the reverse shell.

---

### 🧩 Summary

* ⚠️ MIME type filtering in place
* ❌ No check on actual file content or extension behavior
* ✅ Still exploitable with header manipulation

## ✅ Status

* ⚠️ Exploitable with tools like Burp
* 🟡 Intermediate level
