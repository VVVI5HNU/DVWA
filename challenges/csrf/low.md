🛡️ CSRF – Low Security Level

### 🛠️ Objective:
Exploit an application’s failure to verify the origin of a state-changing request (like changing a password).

---

### 🧭 What Happens Here

On the **Low** level, DVWA provides a password change form without any CSRF protections.

#### 🔍 Observations:
1. Navigate to the CSRF vulnerability page.
2. Enter a new password like `abc123` in both fields and click **"Change"**.
3. Notice the URL:
```

[http://127.0.0.1/DVWA/vulnerabilities/csrf/?password\_new=abc123\&password\_conf=abc123\&Change=Change#](http://127.0.0.1/DVWA/vulnerabilities/csrf/?password_new=abc123&password_conf=abc123&Change=Change#)

````

> ✅ The password is changed directly via a **GET request** with parameters visible in the URL.

---

### ⚠️ Why This is a Vulnerability

- Password change requests should be sent using **POST**, not **GET**.
- No CSRF token is used to validate the request origin.
- A malicious attacker can trick a logged-in user into visiting a crafted URL that changes their password without their knowledge.

#### 💣 Example Attack Link:
```html
<img src="http://127.0.0.1/DVWA/vulnerabilities/csrf/?password_new=hacked&password_conf=hacked&Change=Change#" />
````

---

### 🧩 Summary

* ❌ No CSRF token
* ❌ No method enforcement (uses GET)
* ❌ No origin/referrer checks

## ✅ Status

* ✅ Easily exploitable
* 🟢 Suitable for beginners
