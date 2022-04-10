# 42KL Born2beroot



1. To check if SSH service is started  `(sudo) service ssh status`
2. To check if UFW service is started `(sudo) service ufw status`
3. To enable UFW 'sudo ufw enable'
4. To check UFW port rules 'sudo ufw status numbered'
5. After Step 4, to delete a rule numbered <number> in UFW 'sudo ufw delete <number>'
6. To add back a rule e.g. 4242 'sudo ufw allow <4242>'
7. To check if sudo program is properly installed 'sudo' a help message should pop up
8. To view partition 'lsblk'
9. To add a <user> `sudo adduser <user>`
10. To verify if <user> is created `getent passwd <user>`
11. To create a new <group> `sudo addgroup <group>`
12. To add <user> into a group `sudo adduser <user> <group> OR sudo usermod -aG  <group> <user>`
13. To check if <user> is in a <group> `getent <group> <user>`
14. To view all users in a group `getent group`
15. To switch user `sudo su - <user>`
16. To check current hostname 'hostnamectl'
17. To change hostname to <new_hostname>
    ```
    hostnamectl set-hostname <new_hostname>
    sudo nano /etc/hosts
    
    127.0.0.1 localhost
    127.0.1.1 <new_hostname>
    ```
13. To go back to login page `exit`
14. To reboot VM `sudo reboot`
15. To change password policy 'sudo nano /etc/pam.d/common-password' reboot to take effect
16. To change password expiration 'sudo nano /etc/login.defs' reboot to take effect
17. What is a cron job? 
    ```
    A cron job is a Linux command used for scheduling tasks to be executed sometime in the future. This is
    normally used to schedule a job that is executed periodically – for example, to send out a notice every
    morning.
    ```
18. To set up cron job, add a <name>.sh file in /usr/local/bin/ for a bash script
19. In Born2BeRoot, place the following bash script in the created <name>.sh file
    ```
    #!/bin/bash
    wall $'#Architecture: ' `hostnamectl | grep "Operating System" | cut -d ' ' -f5- ` `awk -F':' '/^model name/            {print $2}' /proc/cpuinfo | uniq | sed -e 's/^[ \t]*//'` `arch` \
$'\n#CPU physical: '`cat /proc/cpuinfo | grep processor | wc -l` \
$'\n#vCPU:  '`cat /proc/cpuinfo | grep processor | wc -l` \
$'\n'`free -m | awk 'NR==2{printf "#Memory Usage: %s/%sMB (%.2f%%)", $3,$2,$3*100/$2 }'` \
$'\n'`df -h | awk '$NF=="/"{printf "#Disk Usage: %d/%dGB (%s)", $3,$2,$5}'` \
$'\n'`top -bn1 | grep load | awk '{printf "#CPU Load: %.2f\n", $(NF-2)}'` \
$'\n#Last boot: ' `who -b | awk '{print $3" "$4" "$5}'` \
$'\n#LVM use: ' `lsblk |grep lvm | awk '{if ($1) {print "yes";exit;} else {print "no"} }'` \
$'\n#Connection TCP:' `netstat -an | grep ESTABLISHED |  wc -l` \
$'\n#User log: ' `who | cut -d " " -f 1 | sort -u | wc -l` \
$'\nNetwork: IP ' `hostname -I`"("`ip a | grep link/ether | awk '{print $2}'`")" \
$'\n#Sudo:  ' `grep 'sudo ' /var/log/auth.log | wc -l`
    ```
16. To edit the timing for cron job interval 
