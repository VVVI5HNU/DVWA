🧨 Blind SQL Injection – Medium Security Level

### 🛠️ Objective:
Use the same Boolean-based blind SQLi logic, but now with hidden parameters in the request.

---

### 🔍 What’s Different?

- Input structure is slightly changed.
- Use **Burp Suite** to inspect and manipulate parameters.

---

### 🧭 Exploitation Steps

1. Use **Burp Suite** to intercept the request after entering a valid ID (e.g., `1`).
2. Locate the `id` parameter in the GET request:
````

id=1

````

3. Inject this payload:
```sql
1' AND SUBSTRING(user,1,1)='a'#
````

4. Forward the request and observe the server response.

✅ If true, you’ll get: `User ID exists...`
❌ If false, response will be: `User ID is missing...`

---

### 🧩 Summary

* ✅ SQLi is still active
* ✅ Requires request interception
* ⚠️ Slight obfuscation of vulnerable input

## ✅ Status

* ✅ Fully exploitable
* 🟡 Requires Burp Suite or manual request editing
