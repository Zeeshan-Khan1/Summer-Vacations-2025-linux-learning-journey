Run the health check as the web server user:

sudo su -s /bin/bash -c "/usr/share/php/passbolt/bin/cake passbolt healthcheck" www-data
A successful setup will report "No issues found!".
