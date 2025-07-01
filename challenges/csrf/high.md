🛡️ CSRF – High Security Level

### 🛠️ Objective:
Analyze if enhanced protections can be bypassed.

---

### 🔍 Observations with Burp Suite

1. Enable the Interceptor in Burp and attempt to change the password.
2. Note that:
   - The request still uses **plain text passwords**.
   - No visible CSRF token is present.
   - The app appears to rely on the session context alone.

3. Right-click the request → **Send to Repeater**
4. Modify the `password_new` and `password_conf` fields.
5. Right-click → **Request in browser → Original session**
6. Paste the generated URL into another browser tab or window.

✅ The password change is accepted, even from another tab — proving it’s vulnerable.

---

### 🧩 Why This Is Still Vulnerable

- No CSRF token is included or validated.
- Origin-based or session-only controls are not sufficient.
- Attackers can create a CSRF attack using the browser’s active session.

---

## ✅ Status
- ⚠️ Still exploitable with same-session abuse
- 🔴 Requires careful observation and manual testing
