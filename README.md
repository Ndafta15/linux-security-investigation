#Linux Security Investigation
## Project Overview
In this project, I built and secured an Ubuntu Linux server in a virtual machine. I configured SSH, a UFW firewall, an Nginx server, and Fail2Ban. I also investigated web and SSH logs to identify failed authentication attempts and understand how suspicious activities can be detected.

## Tool & Technology
-Ubuntu
-SSH
-UFW Firewall
-Nginx
-Faile2Ban
-Linux system logs
-grep,awk,tail,and journalctl

##Security Investigation
I generated a failed SSH login attempt from my host machine to simulate suspicious authentication activity. I then investigated the SSH login and confirmed that Fail2Ban detected the failed attempt.

During the investigation, I:
-Filtered SSH logs for authentication failures.
-Identified the source IP address and targeted username.
-Checked for successful SSH logins from the same IP address.
-Used Fail2Ban to monitor failed SSH authentication attempts.
-Compared failed and successful authentication events to determine whether the activity was suspicious.

##Findings
The failed SSH authentication attempt came from 192.168.64.1, my host machine. Fail2Ban detected one failed attempt byt did not ban the IP because the maximum retry limit was five.
I checked the successful SSH logins and found the same IP had connected successfully. Since it was my knownhost and the failed login was intentionally generated, I determined the activity was not malicious.

## What I Learned
-How SSH provides remote access to a Linux server.
-How UFW controls incoming network traffic.
-How to investigate Nginx and SSH logins.
-How grep,awk,tail,and journalctl filter logs.
-How Fail2Ban detects repeated login failures.
-How to compare log events and determine whether activity is suspicious.
