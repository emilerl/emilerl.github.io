---
title: "Portage Update Checker"
date: 2006-02-27T19:03:31+01:00
draft: false
---

Here is a little script I once wrote to check if new updates exists in the Portage Tree (Gentoo). If so, it sends an e-mail to the owner of the script. Run it as a cron job and don’t forget to change user_address and smtpserver.

```python
#!/usr/bin/python
# Copyright Emil Erlandsson 2005
import os,smtplib

user_address = "receivers address"
smtpserver = "some_smtp_server"

if os.spawnvp(os.P_WAIT, "emerge", ["emerge", "sync"]) == 0:
	pipe = os.popen("emerge -vupD world", "r")
	lines = []
	for line in pipe.readlines():
		if "ebuild" in line:
			lines.append(line)

	if len(lines) > 0:
		hostname = os.popen("hostname", "r").read().strip()
		uptime = os.popen("uptime", "r").read().strip()
		server = smtplib.SMTP(smtpserver)
		msg = "Subject: New updates in your Gentoo distribution @%s\n\nThere are %d new updates.\n\nHere is a list of them:" % (hostname, len(lines))
		for line in lines:
			msg += line
			msg += "\n\n\n/Your local Gentoo Gnome\n\nSysinfo: %s" % uptime
		server.sendmail(user_address,user_address,msg)
		server.close()
else:
	print "emerge sync failed…"
```