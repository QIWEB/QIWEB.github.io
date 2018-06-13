---
layout:     post
title:      start with nginx to proxy your server
subtitle:   nginx Reverse proxy
date:       2018-06-13
author:     LICSLAN
header-img: img/zjm.jpg
catalog: true
tags:
     - tec
     - nginx
---

OK let's using nginx to proxy your server <br>

nginx is very popular proxy server , most companies are using this server to proxy their application, <br>

so let's move to it and learn how to use it  <br>

ok plz make sure you have already install centos7 or other unix os <br>

Preparation work ：  <br>

ssh root@yourIpAddress and login in your system<br>
cd / <br>
mkdir -p /test/nginx<br>
mkdir -p /test/nginx/nginxStart<br>
cd /test/nginx<br>

1.wget http://nginx.org/download/nginx-1.15.0.tar.gz<br>

2.unzip this file such as commond tar -zxvf nginx-1.15.0.tar.gz <br>

3.cd nginx-1.15.0<br>

4.Use the default configuration ./configure <br>

5.or custom configuration (not recommended) so let's use custom configuration<br>

6./configure --prefix=/test/nginx/nginxStart<br>

7.make && make install<br>

8.start or stop nginx server<br>
启动、停止nginx<br>
cd /test/nginx/nginxStart/sbin/<br>
./nginx <br>
./nginx -s stop<br>
./nginx -s quit<br>
./nginx -s reload<br>
./nginx -s quit:此方式停止步骤是待nginx进程处理任务完毕进行停止。<br>
./nginx -s stop:此方式相当于先查出nginx进程id再使用kill命令强制杀掉进程。<br>

9.show nginx pid <br>
ps -ef|grep nginx <br>

ok you are successfully to install nginx server  <br>

10.重启 nginx <br>
10.1.先停止再启动（推荐）： <br>
对 nginx 进行重启相当于先停止再启动，即先执行停止命令再执行启动命令。如下： <br>
./nginx -s quit <br>
./nginx <br>
10.2.重新加载配置文件： <br>
当 ngin x的配置文件 nginx.conf 修改后，要想让配置生效需要重启 nginx，使用-s reload不用先停止  <br>
ngin x再启动 nginx 即可将配置信息在 nginx 中生效，如下： <br>
./nginx -s reload <br>
启动成功后，在浏览器可以看到这样的页面： <br>
nginx-welcome.png <br>
开机自启动 <br>
即在rc.local增加启动代码就可以了。 <br>
vi /etc/rc.local <br>
增加一行 /test/nginx/nginxStart/sbin/nginx <br>
设置执行权限： <br>
chmod 755 rc.local <br>


next look how to Setting up the configuration file---------------- nginx.conf <br>

cd /test/nginx/nginxStart/conf <br>
vim nginx.conf <br>
you wii see <br>
![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/nginx.png)



