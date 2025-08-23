
Edit /etc/caddy/Caddyfile:

:80 {
	# Distribute requests across two upstreams
	reverse_proxy 127.0.0.1:8081 127.0.0.1:8082
}


Reload:

sudo systemctl reload caddy


Visit http://<server-ip> and refresh—requests will be shared.

By default, Caddy uses a load-balancing policy (default: random), and reverse_proxy is the directive that enables it.
