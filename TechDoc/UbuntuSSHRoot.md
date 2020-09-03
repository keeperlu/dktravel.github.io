Enable SSH Root Login
To enable ssh root logging, open the file /etc/ssh/sshd_config.

# vi /etc/ssh/sshd_config
Search for the following line and put the ‘#‘ at the beginning and save the file.

# PermitRootLogin no
Restart the sshd service.

# /etc/init.d/sshd restart
Now try to login with root user.

login as: root
Access denied
root@172.16.25.126's password:
Last login: Tue Nov 20 16:51:41 2012 from 172.16.25.125
[root@tecmint ~]#
