
:80 {
	reverse_proxy {
		to 127.0.0.1:8081 127.0.0.1:8082
		lb_policy weighted_round_robin 5 1
	}
}


Here, :8081 gets ~5x the traffic of :8082.
