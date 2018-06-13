---
layout:     post
title:      linux common commond
subtitle:   linux shell
date:       2018-06-13
author:     LICSLAN
header-img: img/zjm.jpg
catalog: true
tags:
     - tec
     - linux
---


OK let's study linux common commond just like blow<br>

systemctl restart mariadb

systemctl stop mariadb

Vim中如何全选复制粘贴
2015年07月30日 16:37:47
阅读数：15883
Vim中如何全选并复制？ 
（区分大小写！！！） 
全部删除：按esc键后，先按gg（到达顶部），然后dG 
全部复制：按esc键后，先按gg，然后ggyG 
全选高亮显示：按esc键后，先按gg，然后ggvG或者ggVG
单行复制：按esc键后, 然后yy 
单行删除：按esc键后, 然后dd 
粘贴：按esc键后, 然后p
如果不想要行号了，就把set number从/etc/vimrc里删掉就可以了。
dos2unix filename 转换格式 避免windows 命令格式在Linux环境下面报错
安装端口工具包
ftp install  
yum install vsftpd -y
rpm -qa|grep vim 
yum -y install vim* -y
yum install net-tools -y
yum install wget -y
yum install zip unzip -y
yum install lrzsz -y
cp xx ss
mv xx ff
rm -xf xx
 1、firewalld的基本使用
启动： systemctl start firewalld/firewalld.service
查看状态： systemctl status firewalld 
停止： systemctl disable firewalld
禁用： systemctl stop firewalld/firewalld.service
重启：systemctl reload firewalld
#开机启动
systemctl disable firewalld.service/firewalld
systemctl enable iptables.service/firewalld
#开放防火墙端口
firewall-cmd --zone=public --add-port=80/tcp --permanent
firewall-cmd --zone=public --add-port=3306/tcp --permanent
firewall-cmd --zone=public --add-port=6379/tcp --permanent
firewall-cmd --zone=public --add-port=27017/tcp --permanent
firewall-cmd --zone=public --add-port=9102/tcp --permanent
firewall-cmd --zone=public --add-port=2181/tcp --permanent
firewall-cmd --zone=public --add-port=8880/tcp --permanent
firewall-cmd --zone=public --add-port=8765/tcp --permanent
firewall-cmd --zone=public --add-port=81/tcp --permanent
firewall-cmd --zone=public --add-port=8080/tcp --permanent
firewall-cmd --zone=public --add-port=9090/tcp --permanent
firewall-cmd --zone=public --add-port=30000-65535/tcp --permanent
firewall-cmd --zone=public --add-port=20/tcp --permanent
firewall-cmd --zone=public --add-port=21/tcp --permanent

方法1、解压后，根目录里存在dubbo-admin，进入 mvn package -Dmaven.test.skip=true 安装完后，
生成target目录，进入这个目录，找到dubbo-admin-2.6.0这个目录，把这个目录全部copy到tomcat的
目录webapps下的ROOT下面（删除tomcat webapps目录下ROOT原有内容）
方法2、解压后，根目录里存在dubbo-admin，进入 mvn install -Dmaven.test.skip=true 安装完后，
生成target目录，进入这个目录，找到dubbo-admin-2.6.0.war，把这个war包copy到tomcat的目录
webapps下的ROOT下面（删除tomcat webapps目录下ROOT原有内容），
然后使用jar xvf dubbo-admin-2.6.0.war解压war包，把解压后的内容全部放到ROOT目录下
mvn package -Dmaven.test.skip=true
#移除防火墙端口
firewall-cmd --zone=public --remove-port=30000-40000/tcp --permanent
