---
title: 怎么解决LXC容器中OpenWrt dnsmasq的urandom问题
---
用LXC容器安装`OpenWrt 22+`时经常报`/dev/random`错误  
会导致`PPPoE`无法拨号

可以用`vi`编辑`/etc/init.d/dnsmasq`文件  
找到`procd_add_jail_mount /etc/passwd /etc/group /etc/TZ /etc/hosts /etc/ethers`这一行  
在后面添加`/dev/urandom`和`/dev/random`  
举例：`procd_add_jail_mount /etc/passwd /etc/group /etc/TZ /etc/hosts /etc/ethers /dev/urandom /dev/random`  
ps:用`vi`先`Esc`再键入`/jail`可以快速查找  

![改完示意图](1.png)