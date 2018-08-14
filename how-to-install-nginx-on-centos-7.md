---
title: "How to Install Nginx on CentOS 7"
date: 2017-10-31T00:36:30+11:00
tags: [ "CentOS 7", "Nginx"]
categories: ["Operation"]
---
**NGINX** short for Engine X.

# My environment:
+ A CentOS 7 server Minimal install

# Steps
+ 1. Update the system software packages

  ```shell
  yum -y update
  ```
+ 2. Install Nginx HTTP server from the EPEL repository

```shell
yum install epel-release
yum install nginx
```
+ 3. Manage Nginx service

```shell
systemctl start nginx
systemctl enable nginx
systemctl status nginx
```

+ 4. Configure firewalld to allow Nginx traffic

```shell
firewall-cmd --zone=public --permanent --add-service=http
firewall-cmd --zone=public --permanent --add-service=https
firewall-cmd --reload
```

# Important file locations
+ Where the server installed:**/etc/nginx**
+ Main configuration file:**/etc/nginx/nginx.conf**
+ Server block (virtual hosts) configurations can be added in: **/etc/nginx/conf.d**
+ The default server document root directory:**/usr/share/nginx/html**

# Reference
+ [https://www.tecmint.com/install-nginx-on-centos-7/](https://www.tecmint.com/install-nginx-on-centos-7/)
