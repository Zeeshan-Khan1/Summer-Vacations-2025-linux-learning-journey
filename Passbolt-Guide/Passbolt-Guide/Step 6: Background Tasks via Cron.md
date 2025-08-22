To handle email queues and background jobs, add a cron task:

sudo crontab -u www-data -e


Then add:

* * * * * /var/www/passbolt_api/bin/cake EmailQueue.sender
