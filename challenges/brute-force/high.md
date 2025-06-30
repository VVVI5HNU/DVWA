### 🔐 Brute Force – High Security Level

#### 🛠️ Objective:

Bypass an anti-CSRF token mechanism designed to prevent automated brute-force attacks.

---

### 🧭 Key Difference at High Level

* The login form now includes a **dynamic anti-CSRF token** (`user_token`) — a unique, randomly generated alphanumeric value that **changes with each request**.
* This token must be **retrieved and included** in every brute-force request, or the server will reject the login attempt.

---

### ⚙️ Step-by-Step Exploitation Using Burp Suite

#### 1. **Inspect the Anti-CSRF Token**

* Right-click the DVWA login page and open **Inspect**.
* Look for a hidden input field:

  ```html
  <input type="hidden" name="user_token" value="random_token_here">
  ```
* This `user_token` must be dynamically updated in every request sent via Burp Intruder.

---

#### 2. **Set Up Macro to Capture and Insert the Token**

1. **Turn on Interceptor** in Burp and **refresh** the login page.

2. Capture the **GET request** for the login form.

3. Go to **Proxy → Options → Sessions** and click **"Add"** under *Session Handling Rules*.

4. Name your rule, then click **"Add Rule Action"** → choose **"Run a macro"**.

5. Click **"Add"** to create a macro:

   * Choose the request you captured (the login form load).
   * Click **"OK"**.

6. In the **Macro Editor**:

   * Click **"Configure item"** → go to **"Custom Parameter Locations"** → click **"Add"**.
   * Search for `user_token`, and select the correct parameter.
   * Confirm that the token value is automatically highlighted.
   * Click **OK** multiple times to save everything.

7. In **Session Handling Action Editor**:

   * Check the box **"Tolerate URL mismatches"**.

8. In **Session Handling Rule Editor → Scope**:

   * Enable **"Use suite scope"**
   * Enable **"Limit to Intruder"**

---

#### 3. **Prepare Intruder Attack**

1. Refresh the login page, enter any dummy credentials, and intercept the POST request.
2. Go to **HTTP history**, right-click the request, and select **"Send to Intruder"**.
3. Add the Intruder target to **scope** (choose "No" if prompted about changing target scope).

---

#### 4. **Configure the Attack**

1. Mark `username`, `password` fields with `§` symbols as payload positions.
2. Ensure the **`user_token`** field is present in the request — it will now be auto-updated via the macro.
3. Set **Attack Type** to `Cluster Bomb`.

---

#### 5. **Set Payloads**

* **Payload 1 (Username)**:

  * Runtime file: `/usr/share/wordlists/metasploit/http_default_users.txt`

* **Payload 2 (Password)**:

  * File: `/usr/share/wordlists/metasploit/http_default_passwords.txt`

---

#### 6. **Set Response Grepping**

Before launching the attack:

* Go to **"Options" → "Attack Results"**
* Uncheck **"Make unmodified baseline request"**
* Under **"Grep - Match"**, click **"Clear"**
* Add a new grep match string: `incorrect`

---

### ▶️ Launch the Attack

* Click **"Start Attack"**.
* In the results table:

  * Most requests will show a `1` under the **"incorrect"** column, meaning failed login.
  * The correct credentials will show a **blank** in that column — indicating **success**.

---

### ✅ Credentials Found

* **Username:** `admin`
* **Password:** `password`

---

### 🧩 Why This Works

Despite the anti-CSRF token, Burp Suite’s **macro and session handling rules** allow us to:

* Automatically fetch and insert the correct `user_token` in each request.
* Proceed with brute-force attacks as usual.

The security improvements at this level are significant, but still vulnerable to skilled automation with tools like Burp Suite.
