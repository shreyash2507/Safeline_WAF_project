# 🛡️ SafeLine WAF + DVWA Lab

A complete Web Application Firewall (WAF) lab built using **SafeLine WAF**, **Apache2**, and **Damn Vulnerable Web Application (DVWA)** on Ubuntu. The objective of this project was to understand how a reverse proxy WAF protects web applications, how to configure Apache virtual hosts, and how to analyze web traffic through a WAF.

---

## 📖 Project Overview

This project demonstrates the deployment of a vulnerable web application (DVWA) behind SafeLine WAF.

The WAF acts as a reverse proxy that inspects incoming HTTP/HTTPS requests before forwarding them to the Apache web server hosting DVWA.

The project also covers:

- Apache Virtual Host configuration
- Reverse Proxy setup
- HTTPS configuration
- Custom domain configuration
- Hostname resolution
- Port forwarding
- Network troubleshooting
- Request inspection using SafeLine WAF

---

# 🛠️ Technologies Used

- Ubuntu Server
- Apache2
- SafeLine WAF
- DVWA
- PHP
- MySQL / MariaDB
- OpenSSL
- Docker
- Linux Networking
- VirtualBox / VMware
- UFW Firewall

---

# Installation Guide

## Prerequisites

* Ubuntu 22.04 LTS (or later)
* Internet connection
* User with `sudo` privileges

---

# 1. Update the System

```bash
sudo apt update
sudo apt upgrade -y
```

---

# 2. Install Apache

```bash
sudo apt install apache2 -y
```

Enable Apache:

```bash
sudo systemctl enable apache2
sudo systemctl start apache2
```

Verify:

```bash
systemctl status apache2
```

---

# 3. Install MySQL Server

Install MySQL:

```bash
sudo apt install mysql-server -y
```

Enable and start the MySQL service:

```bash
sudo systemctl enable mysql
sudo systemctl start mysql
```

Verify the service is running:

```bash
sudo systemctl status mysql
```

Secure the installation:

```bash
sudo mysql_secure_installation
```

---

# 4. Install PHP

```bash
sudo apt install php php-mysql php-gd php-curl php-xml php-mbstring php-zip libapache2-mod-php -y
```

Verify:

```bash
php -v
```

---

# 5. Restart Apache

```bash
sudo systemctl restart apache2
```

---

# 6. Download DVWA

Navigate to Apache's web directory:

```bash
cd /var/www/html
```

Clone the repository:

```bash
sudo git clone https://github.com/digininja/DVWA.git
```

---

# 7. Configure Permissions

```bash
sudo chown -R www-data:www-data /var/www/html/DVWA
sudo chmod -R 755 /var/www/html/DVWA
```

---

# 8. Configure the Database

Login to MySQLDB:

```bash
sudo mysql
```

Create the database:

```sql
CREATE DATABASE dvwa;

CREATE USER 'dvwa'@'localhost' IDENTIFIED BY 'dvwa123';

GRANT ALL PRIVILEGES ON dvwa.* TO 'dvwa'@'localhost';

EXIT;
```

---

# 9. Configure DVWA

Copy the sample configuration:

```bash
cd /var/www/html/DVWA/config
sudo cp config.inc.php.dist config.inc.php
```

Edit the configuration:

```bash
sudo nano config.inc.php
```

Update the database settings:

```php
$_DVWA['db_server'] = '127.0.0.1';
$_DVWA['db_database'] = 'dvwa';
$_DVWA['db_user'] = 'dvwa';
$_DVWA['db_password'] = 'dvwa123';
```

Save and exit.

---

# 10. Enable Apache Rewrite Module

```bash
sudo a2enmod rewrite
sudo systemctl restart apache2
```

---

# 11. Login

Default credentials:

```
Username: admin

Password: password
```

---

# Installation Complete

DVWA is now installed and ready to be protected behind SafeLine WAF.


---

##TO disable port 80 

Enable the site:

```bash
sudo a2ensite dvwa.conf
sudo systemctl restart apache2
```

---

## Configure Apache to Listen on Port 8080

Edit:

```
/etc/apache2/ports.conf
```

Add:

```apache
#Listen 80
Listen 8080
```

Restart Apache.

```bash
sudo systemctl restart apache2
```

---

## Verify

Apache:

```bash
curl http://127.0.0.1:8080
```

SafeLine:

```bash
curl -k -H "Host: webserver.thebudbax" https://127.0.0.1
```

---

# 📸 Screenshots

## SafeLine Dashboard

---

# 🔍 Troubleshooting Performed

During the project, several issues were encountered and resolved.

### Apache only serving the default page

Resolved by:

- Creating a dedicated VirtualHost
- Configuring DocumentRoot
- Restarting Apache

---

### Apache not listening on 8080

Resolved by:

```
Listen 8080
```

inside

```
/etc/apache2/ports.conf
```

---

### SafeLine showing Website Not Found

Troubleshooting included:

- Checking DNS resolution
- Verifying Host header
- Verifying upstream server
- Checking Apache VirtualHost
- Restarting Apache
- Restarting SafeLine
- Verifying port bindings

---

### HTTPS configuration

Verified SSL communication using

```bash
curl -vk
```

---

# 🧪 Skills Demonstrated

- Web Application Firewall Deployment
- Apache Administration
- Linux Administration
- Virtual Hosts
- HTTPS Configuration
- Reverse Proxy
- Network Troubleshooting
- Hostname Resolution
- Firewall Configuration
- Docker
- Web Security
- DVWA Deployment

---

# 📚 Learning Outcomes

This project helped in understanding:

- How reverse proxy WAFs operate
- HTTP vs HTTPS request flow
- Apache Virtual Host configuration
- Port forwarding
- DNS resolution using hosts file
- SSL/TLS basics
- WAF request inspection
- Secure web application deployment

---

# ⚠️ Disclaimer

This project is intended **only for educational and cybersecurity laboratory purposes**.

DVWA is intentionally vulnerable and should **never** be exposed to the public Internet.

---

# 👨‍💻 Author

**Shreyash**

Cybersecurity Enthusiast

- Linux
- Web Security
- Network Security
- Penetration Testing
- SOC
- Blue Team

---

⭐ If you found this project useful, consider giving it a star!
