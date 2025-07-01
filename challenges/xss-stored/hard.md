🐛 Stored XSS – High Security Level

### 🛠️ Objective:
Attempt to bypass more sophisticated sanitization and filtering to persist XSS code.

---

### 🔍 What’s Different?

- Advanced filtering mechanisms in place.
- Certain characters (like `<`, `>`, `"`) may be encoded automatically.
- Inputs might be passed through a sanitization library.

---

### 🧪 Test Payloads (Advanced)

Try:
```html
<svg/onload=alert(1)>
````

Or:

```html
<details open ontoggle=alert('XSS')>
```

If that fails, try:

1. Intercept the request using **Burp Suite**.
2. Manually encode payloads or insert via a crafted POST request that bypasses client-side validation.

---

### 🧭 Walkthrough

1. Go to **Stored XSS** page.
2. Use Burp Suite to capture the form submission.
3. Replace or encode your payload, such as:

```html
%3Csvg%20onload%3Dalert(1)%3E
```

4. Forward the request and observe the output page.

✅ If payload is stored and executes on viewing, the injection is successful.

---

### 🧩 Summary

* ✅ Advanced sanitization in place
* ⚠️ Exploitable with encoded or obscure payloads
* 🔴 Requires trial-and-error or tool-based injection

## ✅ Status

* ⚠️ May be exploitable
* 🔴 Advanced difficulty
