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

# 🏗️ Architecture

```
                Client Browser
                       │
              HTTPS (443)
                       │
               SafeLine WAF
             Reverse Proxy
                       │
              HTTP (8080)
                       │
                 Apache2
                       │
                    DVWA
```

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

# 📁 Project Structure

```
SafeLine-WAF-DVWA-Lab/

│── README.md
│── LICENSE
│── .gitignore

├── configs/
│     dvwa.conf
│     ports.conf
│     hosts-example.txt
│     ufw-rules.txt
│
├── docs/
│     Project_Report.pdf
│     Troubleshooting_Report.pdf
│
├── screenshots/
│     architecture.png
│     apache.png
│     safeline-dashboard.png
│     dvwa-login.png
│     waf-logs.png
│
└── commands/
      useful-commands.md
```

---

# ⚙️ Installation

## Clone DVWA

```bash
git clone https://github.com/digininja/DVWA.git
```

Move DVWA into Apache's web directory.

```
/var/www/html/DVWA
```

---

## Configure Apache

Create a Virtual Host.

Example:

```apache
<VirtualHost *:8080>

ServerName webserver.thebudbax

DocumentRoot /var/www/html/DVWA

<Directory /var/www/html/DVWA>

AllowOverride All

Require all granted

</Directory>

</VirtualHost>
```

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
Listen 8080
```

Restart Apache.

```bash
sudo systemctl restart apache2
```

---

## Configure SafeLine WAF

Create a new application.

Example configuration:

| Setting | Value |
|---------|-------|
| Domain | webserver.thebudbax |
| HTTPS Port | 443 |
| Upstream | http://192.168.0.111:8080 |

---

## Configure Hosts File

```
192.168.0.111 webserver.thebudbax
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

*(Insert screenshot here)*

---

## Apache Configuration

*(Insert screenshot here)*

---

## DVWA Login

*(Insert screenshot here)*

---

## WAF Request Logs

*(Insert screenshot here)*

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

# 🚀 Future Improvements

- Integrate ModSecurity
- Deploy using Nginx
- Automate deployment using Ansible
- Add Grafana monitoring
- Deploy using Docker Compose
- Configure Let's Encrypt certificates
- Integrate SIEM logging

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
