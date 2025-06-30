# 🛠️ DVWA Setup Guide

This guide explains how to install and run Damn Vulnerable Web Application (DVWA) on your local machine for security testing and challenge walkthroughs.

> ⚠️ **Disclaimer:** DVWA is intentionally insecure. Use it **only** in isolated lab environments. Never expose it to the public internet.

---

## 📦 Option 1: Install DVWA Using Docker (Recommended)

### ✅ Prerequisites
- Docker installed: [Install Docker](https://docs.docker.com/get-docker/)
- Docker Compose (optional but useful)

### 📥 Clone DVWA
```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
````

### ▶️ Start DVWA

```bash
docker-compose up -d
```

### 🌐 Access DVWA

Open your browser and go to:

```
http://localhost:8080
```

### ⚙️ Configure DVWA

1. Click **"Create / Reset Database"**
2. Set **Security Level** (Low, Medium, High, Impossible)
3. Begin testing

---

## 🔧 Option 2: Install DVWA Using XAMPP (Windows/Linux)

### ✅ Prerequisites

* Download and install [XAMPP](https://www.apachefriends.org/index.html)

### 📥 Download DVWA

1. Download DVWA:

   ```bash
   git clone https://github.com/digininja/DVWA.git
   ```
2. Move the `DVWA` folder to:

   * Windows: `C:\xampp\htdocs\`
   * Linux: `/opt/lampp/htdocs/`

### 🛠️ Configure DVWA

1. Rename `config/config.inc.php.dist` to `config.inc.php`
2. Edit the file:

   ```php
   $_DVWA[ 'db_password' ] = 'root';
   ```

### ▶️ Start XAMPP

* Open the XAMPP Control Panel
* Start **Apache** and **MySQL**

### 🌐 Access DVWA

Go to:

```
http://localhost/DVWA/setup.php
```

Click **"Create/Reset Database"**, then go to the login page.

---

## 🐧 Option 3: Manual Setup on LAMP Stack (Ubuntu/Debian)

### ✅ Prerequisites

```bash
sudo apt update
sudo apt install apache2 mysql-server php php-mysqli git
```

### 📥 Setup DVWA

```bash
cd /var/www/html
sudo git clone https://github.com/digininja/DVWA.git
cd DVWA
sudo cp config/config.inc.php.dist config/config.inc.php
sudo chown -R www-data:www-data /var/www/html/DVWA
```

### 🛠️ Configure Database

1. Edit `config.inc.php` and set:

   ```php
   $_DVWA['db_password'] = 'your_mysql_root_password';
   ```
2. Start MySQL and Apache:

   ```bash
   sudo systemctl start apache2
   sudo systemctl start mysql
   ```

### 🌐 Access DVWA

Open:

```
http://localhost/DVWA/setup.php
```

---

## 🔐 Optional Hardening

* Use a virtual machine (e.g., Kali, Parrot, Ubuntu VM)
* Use host-only networking or NAT for isolation
* Reset DVWA frequently when testing destructive exploits

---

## 🧪 Post-Installation Checklist

* [ ] Apache and MySQL are running
* [ ] DVWA loads at `localhost`
* [ ] Database setup completed
* [ ] Security level can be adjusted
* [ ] You’re testing in a **safe, isolated environment**

---

## 🙋 Troubleshooting

* **403 Forbidden?** Check file permissions.
* **No DB connection?** Ensure MySQL is running and the credentials in `config.inc.php` are correct.
* **CSRF token errors?** Clear cookies and refresh the page.

---

## 📎 Useful Links

* DVWA GitHub: [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)
* OWASP Top 10: [https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)
