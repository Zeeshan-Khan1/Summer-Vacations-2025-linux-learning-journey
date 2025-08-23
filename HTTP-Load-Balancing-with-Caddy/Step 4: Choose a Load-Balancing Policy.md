Inside the reverse_proxy block, set one of:

:80 {
	reverse_proxy {
		to 127.0.0.1:8081 127.0.0.1:8082 127.0.0.1:8083
		lb_policy least_conn        # fewest in-flight requests
		# lb_policy round_robin     # cycle through each
		# lb_policy random_choose 2 # choose 2 at random, pick least loaded
	}
}


Policies like least_conn, round_robin, random_choose, plus hashing/sticky options are supported.
