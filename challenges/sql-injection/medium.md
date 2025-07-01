🧨 SQL Injection – Medium Security Level

### 🛠️ Objective:
Find the injectable parameter and exploit it to extract credentials.

---

### 🔍 What's Different?

- SQLi is still possible, but the **input form structure changes**
- The injection point is not obvious — requires inspection via Burp Suite

---

### 🧭 Exploitation Steps

1. Use **Burp Suite** to intercept the request when entering a user ID.
2. In the request, locate the `id` parameter:
````

id=1

````

3. Modify the value to:
```sql
1 UNION SELECT user, password FROM users#
````

4. Forward the request.

✅ The server responds with usernames and passwords from the database.

---

### 🧩 Summary

* ❌ Still lacks proper input validation
* ✅ Requires some manual testing to find the vulnerable parameter
* ⚠️ Slightly obfuscated but fully vulnerable

## ✅ Status

* ✅ Fully exploitable
* 🟡 Intermediate-level challenge
