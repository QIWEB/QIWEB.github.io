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

check your hostname -i is your linux·s ip instead of 127.0.0.1 picture like blow 

if not your linuxs ip (192.168.0.149 or remote server ip) then you can vim /etc/hosts update the setting 

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/img/hostnamei.jpg)

<br>

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/img/hosts.jpg)

then start it like : 

jstatd -J-Djava.security.policy=jstatd.all.policy -J-Djava.rmi.server.hostname=192.168.0.149(or your remote server ip) &

lsof -i:1099(deafault port for jstatd connection)

of courese you should set the firewall and open the port such as 1099 

commond like :firewall-cmd --zone=public --add-port=1099/tcp --permanent   

later commond like : firewall-cmd --reload make it work right

ok now you just double click the visualvm.exe and add remote host input your ip address 

and add jstatd connection

then will show up the reslut just like upon the first picture



3.connect to server or jar using jmx 

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/img/jmx1.jpg)
<br>
![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/img/jmx2.jpg)

cd /your/tomcat/bin/  and  vim catalina.sh

and put code like: 

CATALINA_OPTS="$JAVA_OPTS -Dcom.sun.management.jmxremote 
                       -Dcom.sun.management.jmxremote.port=9010
                       -Dcom.sun.management.jmxremote.authenticate=false
                       -Dcom.sun.management.jmxremote.ssl=false
                       -Djava.rmi.server.hostname=192.168.0.149"

export CATALINA_OPTS

then :wq exit 

ok now you can set the firewall just like upon 

firewall-cmd --zone=public --add-port=9010/tcp --permanent

firewall-cmd --zone=public --add-port=30000-65000/tcp --permanent

firewall-cmd --reload

then you can go to the visualVm to add jmx connection and input your remote ip and port

of course if your ip is not local ip (LAN IP --> local area network such as 192.168.0.XXX) you also should 

setting the security group open port jsut like me using aliyun server (see the picture like blow) and 

setting firwall as well before

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/img/aliyun.jpg)

ok this is to be done if you are doing like upon steps and you will success and see the picture of the first

thanks guys  it is my first tec blog about how to monitor the jvm by using VisualVM.exe to accesss the remote service

ok if you have any problmes welcome send email to licslan@sina.com we can study together and discuss the problem to slove them

best wish to all of you guys 








