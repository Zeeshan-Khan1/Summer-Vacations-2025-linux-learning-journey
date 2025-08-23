
Let’s Encrypt certificates are valid for 90 days, so automatic renewal is required.

Test renewal:

sudo certbot renew --dry-run


Add a cron job for auto-renewal:

sudo crontab -e


Add this line:

0 3 * * * /usr/bin/certbot renew --quiet

🎉 Done!

You now have a free SSL certificate installed and auto-renewed using Let’s Encrypt.
Your website is secure with HTTPS.
