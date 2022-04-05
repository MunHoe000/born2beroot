# 42KL Born2beroot



1. To check if SSH service is started  `(sudo) service ssh status`
2. To check if UFW service is started `(sudo) service ufw status`
3. To add a <user> `sudo adduser <user>`
4. To verify if <user> is created `getent passwd <user>`
5. To create a new <group> `sudo addgroup <group>`
6. To add <user> into a group `sudo adduser <user> <group> OR sudo usermod -aG  <group> <user>`
7. To check if <user> is in a <group> `getent <group> <user>`
8. To view all users in a group `getent group`
9. To switch user `sudo su - <user>`
10. To check current hostname 'hostnamectl'
11. To change hostname to <new_hostname>
    'hostnamectl set-hostname <new_hostname>`
    `sudo nano /etc/hosts`
    '127.0.0.1 localhost`
    `127.0.1.1 <new_hostname>'
10. To reboot VM `sudo reboot`
