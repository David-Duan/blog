---
title: "Setup Virtual Host with Nginx"
date: 2017-10-31T12:53:23+11:00
tags: [ "CentOS 7", "Nginx"]
categories: ["Operation"]
---

Virtual Host, another name "server blocks" in Nginx docs.

# Ready
+ Nginx installed in CentOS 7, as [How to install Nginx on CentOS 7](/post/how-to-install-nginx-on-centos-7/)

# Steps
+ 1.You need 2 folders, one for virtual host configuration files, one for symlink of virtual host configuration files. Nginx configuration file should include the symlink from 2nd folders. So you can enable/disable any virtual host easily.
  - check the 2nd folder location from **/etc/nginx/nginx.conf**
  ```code
  include /etc/nginx/conf.d/*.conf;
  ```

  - create the 1st folder.
  ```shell
  mkdir sites-available
  ```

+ 2.Create virtual host configuration file **/etc/nginx/sites-available/memoledge.com.conf**
```code
server {  
  listen       80;  
  server_name  memoledge.com www.memoledge.com;
  access_log  /var/www/logs/memoledge.access.log;  
  error_log  /var/www/logs/memoledge.error.log error;
  root   /var/www/memoledge.com;  
  index  index.html index.htm;  
}
```

+ 3.Change files permissions and ownership
```shell
chmod 660  /etc/nginx/sites-available/memoledge.com.conf
chgrp nginx  /etc/nginx/sites-available/memoledge.com.conf
```

+ 4.Create folders
```shell
mkdir /var/www
mkdir /var/www/logs
mkdir /var/www/memoledge.com
chgrp nginx /var/www/logs
chgrp nginx /var/www/memoledge.com
find /var/www/ -type d -exec chmod 755 {} \;
find /var/www/ -type f -exec chmod 644 {} \;
```

+ 5.Enable the virtual hosts
```shell
ln -s /etc/nginx/sites-available/memoledge.com.conf /etc/nginx/conf.d/memoledge.com.conf
```

+ 6.Restart Nginx
```shell
nginx -t && systemctl start nginx
```

# Test
+ 1.Put your website or any html pages in **/var/www/memoledge.com**

+ 2.Add following lines in your local laptop "/etc/hosts"
```code
192.168.186.46  www.memoledge.com
192.168.186.46  memoledge.com
```
Now, your website is online.

# Important knowledge
+ Where is the www root:**/var/www**
+ Where is the logs: **/var/www/logs**
+ How to disable a website:
```shell
rm /etc/nginx/conf.d/memoledge.com.conf
```

+ How to enable a website:
```shell
ln -s /etc/nginx/sites-available/memoledge.com.conf /etc/nginx/conf.d/memoledge.com.conf
```

# Reference
+ [https://www.tecmint.com/nginx-name-based-and-ip-based-virtual-hosts-server-blocks/](https://www.tecmint.com/nginx-name-based-and-ip-based-virtual-hosts-server-blocks/)

# TroubleShooting

+ Nginx start failed.
```shell
[root@localhost logs]# systemctl status nginx -l
...
Oct 30 12:53:34 localhost.localdomain nginx[29243]: nginx: [emerg] open() "/var/www/logs/memoledge.access.log" failed (13: Permission denied)
```
You may need to re-run:
```shell
chgrp nginx /var/www/logs
chgrp nginx /var/www/memoledge.com
find /var/www/ -type d -exec chmod 755 {} \;
find /var/www/ -type f -exec chmod 644 {} \;
```

+ 403 forbidden (13: Permission denied)This maybe because:
  - There is no index.html under the root of website
  - Nginx has no permission to access index.html
  ```shell
  find /var/www/ -type d -exec chmod 755 {} \;
  find /var/www/ -type f -exec chmod 644 {} \;
  ```

  - SELinux is enable
  disable SELinux temporally
  ```shell
  setenforce 0
  ```
  disable SELinux forever
  ```shell
  vi /etc/selinux/config
  #SELINUX=enforcing
  SELINUX=disabled
  ```
