# Linux Security Investigation - Commands

These are the primary Linux commands I used while building and investigating my Ubuntu security lab.

## Network Investigation

```bash
hostname -I
ip addr
ping -c 4 8.8.8.8
sudo ss -tulpn

#SSH

sudo systemctl status ssh
ssh victor@192.168.64.2

#UFW Firewall

sudo ufw status
sudo ufw allow OpenSSH
sudo ufw enable
sudo ufw allow 80/tcp
sudo ufw status verbose

#Nginx Web Server

sudo systemctl status nginx
sudo ss -tulpn | grep ':80'

#Web Log Investigation

sudo tail /var/log/nginx/access.log
sudo tail -f /var/log/nginx/access.log
sudo grep '404' /var/log/nginx/access.log
sudo grep -c '404' /var/log/nginx/access.log
sudo awk '{print $7}' /var/log/nginx/access.log
sudo awk '{print $9}' /var/log/nginx/access.log
sudo awk '$9 == 404 {print $1, $7, $9}' /var/log/nginx/access.log

#Fail2Ban

sudo systemctl status fail2ban
sudo fail2ban-client status
sudo fail2ban-client status sshd
sudo fail2ban-client get sshd maxretry

#SSH Log Investigation
sudo journalctl -u ssh --since "10 minutes ago"
sudo journalctl -u ssh | grep "authentication failure"
sudo journalctl -u ssh | grep "Accepted"
