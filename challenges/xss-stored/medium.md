🐛 Stored XSS – Medium Security Level

### 🛠️ Objective:
Bypass basic filters to store persistent JavaScript code in the database.

---

### 🔍 What’s New?

- Basic filters have been added to block tags like `<script>`.
- However, alternate vectors like event handlers or non-standard tags may still succeed.

---

### 🧪 Bypass Payloads

Try injecting:
```html
<img src=x onerror=alert('XSS')>
````

Or:

```html
<svg/onload=alert('XSS')>
```

---

### 🧭 Exploitation Steps

1. Go to **Stored XSS** page.
2. In the `Name` field, use a filtered payload like above.
3. In the `Message` field, write anything.
4. Click **Sign Guestbook**.

✅ If your payload executes and is **persistently displayed**, the injection is successful.

---

### 🧩 Summary

* ⚠️ Basic blacklist filtering (e.g., blocking `<script>`)
* ✅ Still vulnerable with alternate tags or handlers
* 🟡 Intermediate level

## ✅ Status

* ✅ Still exploitable
* 🟡 Requires creative bypass
