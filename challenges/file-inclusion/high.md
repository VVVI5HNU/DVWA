📂 File Inclusion – High Security Level

### 🛠️ Objective:
Understand and attempt to bypass advanced file inclusion restrictions.

---

### 🔒 What’s New?

The source code now:
- Only allows filenames like `include.php`
- Or files that start with `file`

This restricts arbitrary file inclusion.

---

### 🧭 LFI with `file://` URI

Try:
```bash
page=file:///etc/passwd
````

✅ If allowed, this may still read local files using a URI scheme.

However, attempts to include remote files (e.g., via `http://`) are blocked.

---

### 🚫 RFI Blocked

Due to strict pattern matching, **remote file inclusion is no longer possible** at this level.

---

### 🧩 Summary

* ✅ LFI may still be possible via `file://`
* ❌ RFI blocked
* ✅ Source validation and pattern enforcement implemented

## ✅ Status

* ⚠️ Partially exploitable (LFI only)
* 🔴 Requires careful testing and knowledge of file schemes
