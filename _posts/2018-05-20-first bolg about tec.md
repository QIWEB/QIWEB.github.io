---
layout:     post
title:      let`s monitor the jvm by using VisualVM.exe to accesss the remote service
subtitle:   jvm tomcat java
date:       2018-05-29
author:     LICSLAN
header-img: img/zjm.jpg
catalog: true
tags:
    - tec
    - about jvm
---


ok next write something about how to connect the remote server and monitor the cpu & memory & GC 

blow the picture is about jvm & GC

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/img/jvm.png)

<br>

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/img/gc.jpg)

if you want to see the picture like upon , so there something you should prepare for it 

install VM(virtual machine) in your computer then install linux os such as centos7 & ubantu etc

before connect to the local server & remote server plz make sure you set the right environment like bolw setps 

1.set the jdk Environment variables [plz baidu yiha &rarr;](https://www.baidu.com/) if it is work right  you will see like this  

(command like : java -version / java)

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/img/jdk.jpg)

2.connect to server or jar using jstatd 

cd /your/jdk/bin/  and  vim jstatd.all.policy

wirte something like : grant codebase "file:${java.home}/../lib/tools.jar" {permission java.security.AllPermission;};

check you hostname -i is your linux·s ip instead of 127.0.0.1 picture like blow if not your linux`s ip(192.168.0.149 or remote server 

ip) then you can vim /etc/hosts update the setting  
 
then start it like : jstatd -J-Djava.security.policy=jstatd.all.policy -J-Djava.rmi.server.hostname=192.168.0.149(or your remoter server ip) &

lsof -i:1099(deafault port for jstatd connection)

of courese you should set the firewall and open the port such as 1099 commond like :firewall-cmd --zone=public --add-port=1099/tcp --

permanent   later commond like : firewall-cmd --reload make it work right

ok now you just double click the visualvm.exe and add remote host input your ip address 

and add jstatd connection

then will show up the reslut just like upon the first picture



3.connect to server or jar using jmx 




