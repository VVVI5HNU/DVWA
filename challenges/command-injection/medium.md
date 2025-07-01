# 🧨 Command Injection – Medium Security Level

### 🛠️ Objective:
Bypass basic filtering to execute commands via system shell.

---

### 🔒 What’s Different?

The application now **blacklists common command chaining operators** like `;` and `&&`.

---

### 🧭 Bypass Techniques

Although `;` and `&&` are blocked, alternatives like the **pipe symbol (`|`)** and logical OR (`||`) may still be accepted.

#### 💣 Example Payloads:
```bash
127.0.0.1 | ls
127.0.0.1 | cat /etc/passwd
127.0.0.1 || whoami
````

---

### 🧩 Why This Works

DVWA uses a **basic blacklist** approach that filters only specific characters. However, the shell has **multiple command separators**, and the filter can often be bypassed with alternatives.

---

## ✅ Status

* ⚠️ Still exploitable
* 🟡 Intermediate level required
