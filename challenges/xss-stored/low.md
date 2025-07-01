🐛 Stored XSS – Low Security Level

### 🛠️ Objective:
Inject persistent JavaScript code that gets stored in the database and executed when any user views the affected page.

---

### 🧭 Walkthrough

1. Go to the **Stored XSS** page in DVWA.
2. In the `Name` field, input:
```html
<script>alert('XSS')</script>
````

3. Enter anything in the `Message` field.
4. Click **Sign Guestbook**.

✅ After submitting, the alert box will pop up — and will also execute **whenever anyone else visits the page**.

---

### 🧪 Alternate Payloads

* `<img src=x onerror=alert('XSS')>`
* `<svg/onload=alert('Stored XSS')>`
* `<marquee onstart=alert(1)>XSS</marquee>`

---

### 🧩 Summary

* ❌ No sanitization
* ✅ Input is stored and reflected directly
* 🟢 Very beginner-friendly

## ✅ Status

* ✅ Fully exploitable
* 🟢 Ideal for learning persistent XSS basics
