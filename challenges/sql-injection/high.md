🧨 SQL Injection – Hard Security Level

### 🛠️ Objective:
Exploit SQL injection in a more protected or hidden UI flow.

---

### 🔍 What's New?

- The injection point is behind a button or separate prompt (e.g., “Click here to change ID”).
- Application structure is slightly more layered, but still vulnerable.

---

### 🧭 Exploitation Steps

1. Click the **"Click here to change ID"** button.
2. A new input prompt appears — enter the following payload:
   ```sql
   ' UNION SELECT user, password FROM users#
````

3. Submit the form.
4. Check the output — user credentials are shown.

✅ Even with UI changes, SQL injection remains exploitable.

---

### 🧩 Summary

* ⚠️ Minor interface obfuscation
* ❌ No true SQLi protection
* ✅ Same payload as Medium works

## ✅ Status

* ✅ Fully exploitable
* 🔴 Requires basic understanding of where input flows
