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
systemctl restart mariadb<br>
systemctl stop mariadb<br>
Vim中如何全选复制粘贴<br>
Vim中如何全选并复制？ <br>
（区分大小写！！！） <br>
全部删除：按esc键后，先按gg（到达顶部），然后dG <br>
全部复制：按esc键后，先按gg，然后ggyG <br>
全选高亮显示：按esc键后，先按gg，然后ggvG或者ggVG<br>
单行复制：按esc键后, 然后yy <br>
单行删除：按esc键后, 然后dd <br>
粘贴：按esc键后, 然后p<br>
如果不想要行号了，就把set number从/etc/vimrc里删掉就可以了。<br>
dos2unix filename 转换格式 避免windows 命令格式在Linux环境下面报错<br>
安装端口工具包<br>
ftp install  <br>
yum install vsftpd -y<br>
rpm -qa|grep vim <br>
yum -y install vim* -y<br>
yum install net-tools -y<br>
yum install wget -y<br>
yum install zip unzip -y<br>
yum install lrzsz -y<br>
cp xx ss<br>
mv xx ff<br>
rm -xf xx<br>
 1、firewalld的基本使用<br>
启动： systemctl start firewalld/firewalld.service<br>
查看状态： systemctl status firewalld <br>
停止： systemctl disable firewalld<br>
禁用： systemctl stop firewalld/firewalld.service<br>
重启：systemctl reload firewalld<br>
#开机启动<br>
systemctl disable firewalld.service/firewalld<br>
systemctl enable iptables.service/firewalld<br>
#开放防火墙端口<br>
firewall-cmd --zone=public --add-port=80/tcp --permanent<br>
firewall-cmd --zone=public --add-port=3306/tcp --permanent<br>
firewall-cmd --zone=public --add-port=6379/tcp --permanent<br>
firewall-cmd --zone=public --add-port=27017/tcp --permanent<br>
firewall-cmd --zone=public --add-port=9102/tcp --permanent<br>
firewall-cmd --zone=public --add-port=2181/tcp --permanent<br>
firewall-cmd --zone=public --add-port=8880/tcp --permanent<br>
firewall-cmd --zone=public --add-port=8765/tcp --permanent<br>
firewall-cmd --zone=public --add-port=81/tcp --permanent<br>
firewall-cmd --zone=public --add-port=8080/tcp --permanent<br>
firewall-cmd --zone=public --add-port=9090/tcp --permanent<br>
firewall-cmd --zone=public --add-port=30000-65535/tcp --permanent<br>
firewall-cmd --zone=public --add-port=20/tcp --permanent<br>
firewall-cmd --zone=public --add-port=21/tcp --permanent<br>

方法1、解压后，根目录里存在dubbo-admin，进入 mvn package -Dmaven.test.skip=true 安装完后，<br>
生成target目录，进入这个目录，找到dubbo-admin-2.6.0这个目录，把这个目录全部copy到tomcat的<br>
目录webapps下的ROOT下面（删除tomcat webapps目录下ROOT原有内容）<br>
方法2、解压后，根目录里存在dubbo-admin，进入 mvn install -Dmaven.test.skip=true 安装完后，<br>
生成target目录，进入这个目录，找到dubbo-admin-2.6.0.war，把这个war包copy到tomcat的目录<br>
webapps下的ROOT下面（删除tomcat webapps目录下ROOT原有内容），<br>
然后使用jar xvf dubbo-admin-2.6.0.war解压war包，把解压后的内容全部放到ROOT目录下<br>
mvn package -Dmaven.test.skip=true<br>
#移除防火墙端口<br>
firewall-cmd --zone=public --remove-port=30000-40000/tcp --permanent<br>
cat catalina.out |grep "MessageBrokerImpl save message succeeded"
ps -ef|grep tomcat
find / -name ""
rz (上传) sz （下载）
cp -r /test /xx
mv filename /xx
mv filename anotherfilename

