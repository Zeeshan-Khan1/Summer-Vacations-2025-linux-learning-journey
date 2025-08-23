Verify & Operate

Check status/logs:

systemctl status caddy
journalctl -u caddy --no-pager | less +G


Reload after edits:

sudo systemctl reload caddy


These are the recommended service-management steps.
