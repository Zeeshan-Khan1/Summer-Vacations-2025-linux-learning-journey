Production HTTPS (automatic TLS)

Point your DNS (e.g., lb.example.com) to this server, then:

lb.example.com {
	encode zstd gzip
	reverse_proxy 10.0.0.11:8080 10.0.0.12:8080
}


Caddy will automatically obtain and renew certificates and serve HTTPS on :443. 
Caddy Web Server

Reload:

sudo systemctl reload caddy
