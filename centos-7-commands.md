# File
```shell
#Copy file to remote server
scp -r /Users/hugo/blog/public/* root@192.168.186.46:/var/www/memoledge.com/
```
# User
```shell
#add user
adduser phpq
#set password
passwd phpq
#add group
groupadd test
#add user to group
useradd -g test phpq
#asign user to a single group
usermod -G groupname username
#asign user to another goup
usermod -a groupname username
#remove user from group
gpasswd -d A GROUP
#show user detail
id user
cat /etc/passwd
#delete user
userdel peter
#delete group
groupdel peter
```

# Service
```shell
#list all services
systemctl list-unit-files
#service and listening port
cat /etc/services | grep 834
```

# Network
```shell
#service and listening port
cat /etc/services | grep 834
#open port
sudo firewall-cmd --zone=public --add-port=80/tcp --permanent
sudo firewall-cmd --reload
#check all rules
firewall-cmd --list-all
```
