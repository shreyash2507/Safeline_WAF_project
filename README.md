# 🛡️ SafeLine WAF + DVWA Lab

![image alt](https://github.com/shreyash2507/Safeline_WAF_project/blob/6b2742c3b7c8f36418b6383b70426c705768a791/Banner.png)

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
