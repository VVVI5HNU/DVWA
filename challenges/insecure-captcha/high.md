🤖 Insecure CAPTCHA – High Security Level

### 🛠️ Objective:
Bypass advanced validation logic that includes user-agent and CAPTCHA token checks.

---

### 🔍 Observations from Source Code

- Requires:
  - `g-recaptcha-response == hidd3n_valu3`
  - `User-Agent == reCAPTCHA`

---

### 🧭 Exploitation Steps

1. Enable Burp Intercept and submit the form with any values.
2. Modify the following in the captured request:

   - **Set the User-Agent header**:
     ```
     User-Agent: reCAPTCHA
     ```

   - **Add or modify this parameter** in the request body:
     ```
     g-recaptcha-response=hidd3n_valu3
     ```

3. Forward the request.

✅ CAPTCHA logic is bypassed, and password is successfully updated.

---

### 🧩 Summary

- ✅ CAPTCHA check depends on fixed token and user-agent string
- ❌ No real CAPTCHA verification mechanism
- ✅ Still exploitable with full control of request

## ✅ Status
- ⚠️ More advanced, but still bypassable
- 🔴 Requires inspection and manipulation of headers and POST data
