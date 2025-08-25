# 🔐 Free SSL Certificate Setup Guide (Let's Encrypt)

This guide explains how to set up a **free SSL certificate** for your website using **Let’s Encrypt** and **Certbot**. After following these steps, your site will run securely on **HTTPS**.

---

## ✅ Prerequisites
- A server running **Linux** (Ubuntu, Debian, AlmaLinux, CentOS, etc.).
- A **domain name** pointing to your server’s IP (e.g., `example.com`).
- A running **web server** (**Apache** or **Nginx**).
- Root or sudo access.

---

## ⚡ Step 1: Install Certbot

### Ubuntu/Debian
````bash
sudo apt update
sudo apt install certbot python3-certbot-nginx -y   # for Nginx
sudo apt install certbot python3-certbot-apache -y  # for Apache

CentOS / AlmaLinux / RHEL
sudo dnf install epel-release -y
sudo dnf install certbot python3-certbot-nginx -y   # for Nginx
sudo dnf install certbot python3-certbot-apache -y  # for Apache
