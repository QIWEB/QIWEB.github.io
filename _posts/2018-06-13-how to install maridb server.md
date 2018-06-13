---
layout:     post
title:      how to install mariadb(mysql) server
subtitle:   SQL MYSQL mariadb 
date:       2018-06-13
author:     LICSLAN
header-img: img/zjm.jpg
catalog: true
tags:
     - tec
     - sql databases
---


OK let's bulid our free databases server Mariadb <br>

next i will use chinese to describe how to build your own mariadb server<br>
首先在CentOS 7.0安装MariaDB的数据库，在这里记录下安装过程，以便以后查看。<br>
1、安装MariaDB<br>
安装命令<br>
yum -y install mariadb mariadb-server
卸载数据库：<br>
root@localhost logs# yum -y remove mari*
安装完成MariaDB，首先启动MariaDB<br>
systemctl start mariadb
设置开机启动<br>
systemctl enable mariadb
接下来进行MariaDB的相关简单配置<br>
mysql_secure_installation
首先是设置密码，会提示先输入密码<br>
Enter current password for root (enter for none):<–初次运行直接回车
设置密码<br>
Set root password? [Y/n] <– 是否设置root用户密码，输入y并回车或直接回车<br>
New password: <– 设置root用户的密码<br>
Re-enter new password: <– 再输入一次你设置的密码<br>
其他配置<br>
Remove anonymous users? [Y/n] <– 是否删除匿名用户，回车<br>
Disallow root login remotely? [Y/n] <–是否禁止root远程登录,回车,<br>
Remove test database and access to it? [Y/n] <– 是否删除test数据库，回车<br>
Reload privilege tables now? [Y/n] <– 是否重新加载权限表，回车<br>
初始化MariaDB完成，接下来测试登录<br>
mysql -u root -p<br>
完成。<br>
2、配置MariaDB的字符集<br>
文件/etc/my.cnf<br>
vim /etc/my.cnf<br>
在[mysqld]标签下添加<br>
init_connect='SET collation_connection = utf8_unicode_ci' <br>
init_connect='SET NAMES utf8' <br>
character-set-server=utf8 <br>
collation-server=utf8_unicode_ci <br>
skip-character-set-client-handshake<br>
文件/etc/my.cnf.d/client.cnf<br>
vim /etc/my.cnf.d/client.cnf<br>
在[client]中添加<br>
default-character-set=utf8<br>
文件/etc/my.cnf.d/mysql-clients.cnf<br>
vim /etc/my.cnf.d/mysql-clients.cnf<br>
在[mysql]中添加<br>
 全部配置完成，重启mariadb<br>
systemctl restart mariadb<br>
之后进入MariaDB查看字符集<br>
mysql> show variables like "%character%";show variables like "%collation%";<br>
显示为<br>

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/dbsql.png)

字符集配置完成。<br>

授予外网登陆权限 <br>
mysql>grant all privileges on *.* to username@'%' identified by 'password';
