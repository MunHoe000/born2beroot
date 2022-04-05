# 42KL Born2beroot



1. To check if SSH service is started  `(sudo) service ssh status`
2. To check if UFW service is started `(sudo) service ufw status`
3. To add a <user> `sudo adduser <user>`
4. To verify if <user> is created `getent passwd <user>`
  ### To create a new `group`
```
sudo addgroup <group>
```
### To add `user` into a group
```
sudo adduser <user> <group>

or 

sudo usermod -aG  <group> <user>
```
### To check if `user` is in a `group`
```
getent <group> <user>
```
### To view all users in a group
```
getent group
```
### To switch user
```
sudo su - <user>
```

### To reboot
```
sudo reboot
```
