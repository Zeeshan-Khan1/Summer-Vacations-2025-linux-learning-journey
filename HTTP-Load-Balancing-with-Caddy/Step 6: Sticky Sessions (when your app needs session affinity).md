

If your app keeps session state in-memory, enable stickiness via cookie:

:80 {
	reverse_proxy {
		to 127.0.0.1:8081 127.0.0.1:8082

		# First request gets a cookie that "sticks" the client to an upstream
		lb_policy cookie mylb supersecret
	}
}


Caddy sets/reads a cookie (default name lb) to map clients to the same upstream while it’s available. (Use your own secret.) This cookie is only for load balancing/affinity, not authentication.
