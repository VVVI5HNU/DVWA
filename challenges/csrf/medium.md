🛡️ CSRF – Medium Security Level

### 🛠️ Objective:
Bypass basic CSRF defenses and change the password.

---

### 🔒 What’s Different?

- Direct GET-based attacks no longer work.
- Error shown: `"That request didn't look correct."`

### 🔍 Protection Used:
- DVWA now checks the **HTTP Referer header** to verify that the request came from its own domain.

---

### 🧭 Exploiting with Burp Suite

1. Submit a valid password change request in DVWA.
2. In **Burp Suite**, intercept the request and note that the **Referer header** is present:
````

Referer: [http://127.0.0.1/DVWA/vulnerabilities/csrf/](http://127.0.0.1/DVWA/vulnerabilities/csrf/)

```

3. Craft your own request to change the password and **manually add the Referer** header to match the DVWA origin.

4. Forward the request. The password will be changed successfully.

---

### 🧩 Why This Works

- DVWA relies solely on the **Referer header** for CSRF protection.
- The Referer header can be easily spoofed using tools like Burp Suite.

## ✅ Status
- ⚠️ Still exploitable with header manipulation
- 🟡 Requires intermediate knowledge
