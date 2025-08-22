
# Passbolt CE Setup Guide

A complete, step-by-step guide to **install and configure Passbolt Community Edition (CE)**—a secure, open-source password manager—for your team.

---

##  Prerequisites

- Ubuntu 24.04 server (clean, minimal install)  
- At least **2 CPU cores** and **2 GB RAM** (recommended)  
- A **domain name** pointing to your server or a static IP  
- Working **SMTP server** for email notifications  
- **NTP** configured to ensure consistent time (required for GPG)  
:contentReference[oaicite:0]{index=0}

---

##  Step 1: Add Passbolt Repository & Install Package

```bash
cd /tmp
curl -LO https://download.passbolt.com/ce/installer/passbolt-repo-setup.ce.sh
curl -LO https://github.com/passbolt/passbolt-dep-scripts/releases/latest/download/passbolt-ce-SHA512SUM.txt
sha512sum -c passbolt-ce-SHA512SUM.txt && sudo bash ./passbolt-repo-setup.ce.sh
sudo apt update
sudo apt install passbolt-ce-server
