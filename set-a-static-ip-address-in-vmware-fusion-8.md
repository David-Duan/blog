---
title: "Set a Static Ip Address in VMware Fusion 8"
date: 2017-11-03T20:14:56+11:00
tags: [ "Mac", "VMware Fusion 8"]
categories: ["Operation"]
---
# Environment
+ Mac Book
+ Host: VMware Fusion 8
+ Guest: CentOS 7

# Issue
Always got different IP address when come to office or back home.

# Solution
+ 1.User NAT for network traffic
+ 2.Make VMware Fusion 8 alway assign the specific IP address.

# Steps
+ 1.Shutdown the virtual mechine and copy its MAC address.
![image1](/post/images/set-static-ip-address-in-vmware-fusion-8-1.png)
+ 2.Modify dhcpd.conf
```shell
sudo nano /Library/Preferences/VMware\ Fusion/vmnet8/dhcpd.conf
```
Add following at the end.
```code
host playground {
    hardware ethernet 00:0C:29:B6:22:3E;
    fixed-address  192.168.167.80;
}
```
**playground** is the virtual machine's name

+ 3.Restart VMware Fusion
+ 4.Start the VM and check the IP address

# Reference
+ [https://willwarren.com/2015/04/02/set-static-ip-address-in-vmware-fusion-7/](https://willwarren.com/2015/04/02/set-static-ip-address-in-vmware-fusion-7/)
