

Active health checks (probe a path on a timer):

:80 {
	reverse_proxy {
		to 127.0.0.1:8081 127.0.0.1:8082
		lb_policy least_conn

		# Active checks: mark an upstream unhealthy if /health fails
		health_uri /health
		health_interval 15s
		health_timeout 5s
		health_status 200
	}
}


Passive health checks (auto-mark failing/up-slow backends):

:80 {
	reverse_proxy {
		to 127.0.0.1:8081 127.0.0.1:8082
		fail_duration 30s   # remember a failure for this long
		max_fails 3         # 3 fails in the window => unhealthy
	}
}


Health-check directives and behavior are built into reverse_proxy
