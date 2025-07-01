🤖 Insecure CAPTCHA – Medium Security Level

### 🛠️ Objective:
Bypass improved CAPTCHA validation using request manipulation.

---

### 🔒 What's New?

The backend now checks for a new parameter:
```

passed\_captcha=true

```

---

### 🧭 Exploit via Burp Suite

1. Intercept the password change request via Burp.
2. Modify:
```

step=1 → step=2

```

3. At the end of the request body (after `&Change=Change`), append:
```

\&passed\_captcha=true

```

4. Forward the request.

✅ CAPTCHA bypassed again, and password changes successfully.

---

### 🧩 Summary

- ❌ Still no CAPTCHA engine involved
- ✅ Simply accepting `passed_captcha=true` is enough
- ✅ Easily spoofable

## ✅ Status
- ⚠️ Exploitable with minimal header manipulation
- 🟡 Intermediate
