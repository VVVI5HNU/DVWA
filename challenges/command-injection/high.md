 🧨 Command Injection – High Security Level

### 🛠️ Objective:
Defeat an enhanced blacklist with stricter command filtering.

---

### 🔒 What’s Different?

- The input is filtered more aggressively.
- More dangerous characters (e.g., `;`, `&&`, `|`, `||`) are blacklisted.
- DVWA may also attempt to strip or escape commands based on known patterns.

---

### 🧭 Bypass Strategy

The trick lies in understanding how the filter is applied — in this case, **spaces** may trigger filtering, but **removing the space** after a symbol like `|` might bypass it.

#### 🔍 Observations:
- `| pwd` → ❌ No output
- `|pwd` → ✅ Output returned

#### 💣 Example Payloads:
```bash
127.0.0.1|pwd
127.0.0.1|ls
127.0.0.1|whoami
````

---

### 🧩 Why This Works

The input filter may only blacklist specific patterns like `"| "` (pipe followed by space), allowing variants like `"|pwd"` to slip through.

---

## ✅ Status

* ⚠️ Still exploitable with obfuscation
* 🔴 Requires attention to syntax and filter behavior
