### 🔓 Brute Force – Low Security Level

#### 🛠️ Objective:

Exploit a login form that lacks basic security protections, such as rate limiting, input validation, or account lockout.

---

### 🧭 Step-by-Step Exploitation Using Burp Suite

1. **Launch Burp Suite**

   * Open Burp Suite and go to the **Proxy** tab.
   * Click **"Open Browser"** and ensure **Interceptor** is turned on.

2. **Capture the Login Request**

   * In the browser, navigate to the DVWA login page.
   * Enter any random credentials (e.g., `test:test`) and submit the form.
   * The request will be intercepted by Burp.

3. **Send the Request to Intruder**

   * In Burp, right-click the intercepted request and select **"Send to Intruder"**.

4. **Configure the Attack**

   * Go to the **Intruder** tab.
   * Identify and select the **username** and **password** fields in the request body.
   * Click **"Add §"** to mark these as payload positions.
   * Set the **Attack Type** to `Cluster Bomb` (to test different combinations of usernames and passwords).

5. **Set Payloads**

   * Payload 1 (username field):

     * Set **Payload Type** to `Runtime file`.
     * Load from:
       `/usr/share/wordlists/metasploit/http_default_users.txt`
   * Payload 2 (password field):

     * Load from:
       `/usr/share/wordlists/metasploit/http_default_passwords.txt`

6. **Start the Attack**

   * Click **"Start Attack"** and monitor the results.

---

### 📊 Analyzing the Results

* Observe the **"Length"** column in the results table.
* Most requests will have a similar content length, indicating failed login attempts.
* However, when the **username is `admin`** and the **password is `password`**, the response has a **notably higher length**, suggesting a successful login.

---

### ✅ Credentials Found

* **Username:** `admin`
* **Password:** `password`

---

### 🧩 Why This Works

At the low security level, DVWA does not implement:

* CAPTCHA
* Account lockout
* Brute-force protection mechanisms

This allows tools like Burp Suite Intruder to automate credential guessing easily.

---

Would you like a similar format for Medium/High/Impossible levels too? I can help create a full set of walkthroughs in the same professional tone.

