### 🔐 Brute Force – Medium Security Level

#### 🛠️ Objective:

Exploit a login form that introduces basic protection through delayed responses to slow down brute-force attacks.

---

### 🧭 Step-by-Step Exploitation Using Burp Suite

1. **Identify the Key Difference**

   * View the **page source** of the login form.
   * Scroll down and observe that after a failed login attempt, the server executes a `sleep(2)` command.
   * This introduces a **2-second delay** per attempt, making brute-force attacks slower but not impossible.

2. **Launch Burp Suite**

   * Open Burp Suite → Go to **Proxy** → **Open Browser** (with Interceptor on).

3. **Capture the Request**

   * Enter any credentials on the login page.
   * Intercept the request in Burp and send it to **Intruder**.

4. **Configure the Attack (Same as Low Level)**

   * Select the **username** and **password** fields and mark them as payload positions (`§`).
   * Set **Attack Type** to `Cluster Bomb`.

5. **Set Payloads**

   * **Payload 1 (Username):**

     * Type: Runtime file
     * File: `/usr/share/wordlists/metasploit/http_default_users.txt`
   * **Payload 2 (Password):**

     * File: `/usr/share/wordlists/metasploit/http_default_passwords.txt`

6. **Start the Attack**

   * Initiate the attack.
   * Observe that each request now takes approximately **2000 ms (2 seconds)** to respond due to the delay.

---

### 📊 Analyzing the Results

* Monitor the **"Length"** column in the Intruder results.
* Despite the delay, the correct credentials will still cause a **noticeably different response length**.
* This indicates a successful login.

---

### ✅ Credentials Found

* **Username:** `admin`
* **Password:** `password`

---

### 🧩 Why This Works

While DVWA at medium level attempts to slow brute-force attacks using a fixed delay (`sleep(2)`), it doesn't:

* Block repeated attempts
* Implement rate limiting
* Randomize delays or response messages

As a result, attackers can still use time-based analysis and response length patterns to find valid credentials.
