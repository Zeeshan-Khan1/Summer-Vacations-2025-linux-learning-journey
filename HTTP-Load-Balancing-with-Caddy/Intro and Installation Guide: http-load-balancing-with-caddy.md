🌐 HTTP Load Balancing with Caddy

What is Load Balancing?
Load balancing means distributing incoming network traffic across multiple servers. This helps:

Improve website speed.

Prevent server overload.

Ensure high availability (if one server fails, traffic goes to another).

What is Caddy?
Caddy is a modern, open-source web server (like Nginx or Apache) but easier to configure. It comes with:

Automatic HTTPS (SSL/TLS).

Simple configuration file (Caddyfile).

Built-in reverse proxy and load balancing features.

HTTP Load Balancing with Caddy Example:

Caddy can be used to distribute HTTP requests between multiple backend servers:

:80 {
    reverse_proxy localhost:8081 localhost:8082 localhost:8083
}


👉 This means:

Caddy listens on port 80 (HTTP).

It will forward requests to servers running on 8081, 8082, 8083.

If one server is down, traffic will go to the next available one.

Benefits of Using Caddy for Load Balancing:

Super simple setup (just one config line).

Built-in health checks.

Works with HTTPS out of the box.

Supports round robin, least connections, and more.

---

## 1) Prerequisites

- A Linux server (Ubuntu/Debian/AlmaLinux/CentOS etc.)
- `sudo` access
- Two or more backend apps (e.g., on `:8081`, `:8082`, …)

---

## 2) Install Caddy

### Ubuntu / Debian (official repo)
```bash
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https curl
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' \
  | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' \
  | sudo tee /etc/apt/sources.list.d/caddy-stable.list
chmod o+r /usr/share/keyrings/caddy-stable-archive-keyring.gpg
chmod o+r /etc/apt/sources.list.d/caddy-stable.list
sudo apt update
sudo apt install caddy
This installs Caddy and sets it up as a systemd service 
