---
layout:     post
title:      how to build your own gitlab server (gogs)
subtitle:   java git
date:       2018-06-01
author:     LICSLAN
header-img: img/zjm.jpg
catalog: true
tags:
    - tec
    - about git
---


Happy children's day !! I want go back to 90's if i can <br>

ok let's get to the right point 

blow the picture is about git gogs server

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/gogs1.jpg)

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/gogs2.jpg)<br>

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/gogs3.jpg)

![](https://raw.githubusercontent.com/licslan/licslan.github.io/master/gogs4.jpg)<br>

next i will intorduce how to use git commod <br>

of course it's sort of base commod such as you can download code or file from your server<br>

for example github 码云 gogs you also can upload files to the server<br>

ok the first thing you should do is down git/git bash etc as you can input git commod<br>

you also need to study git commod [plz go here &rarr;](http://git.mydoc.io/)<br>

before you start building gogs server plz make sure you have already installed mysql(mariadb) server<br>

plz see my another blog about how to install mariadb server on linux os<br>

ok  let's to right point start installing gogs server<br>

The installation process is as follows<br>

1.add a new user for gogs server unless you want to use root as your first gogs's user is not safe!!!<br>

2.Download Source Code Compile / Download Precompiled Binary Package<br>

3.Run the installation<br>

4.Configuration adjustment<br>

5.Configure the nginx reverse proxy<br>

6.Keep the service running<br>

Note that by default you have already installed MySQL server (or MariaDB) and nginx. If not, <br>

find out how to install and configure these dependencies. Of course, you can also use the SQLite db.<br>

next we use centos7 as project envirment <br>

【add user】 : useradd git   ------->   sudo su git <br> 

【Download Source Code Compile】: <br>

cd /home/git/path you mkdir -p dir name/   ------><br>

yum install wget -y  (make sure you have installed wget)  ------><br>

wget https://github.com/gogs/gogs/releases/download/v0.11.43/linux_amd64.tar.gz  -----><br>
 
tar zxvf linux_amd64.tar.gz -----> cd  linux_amd64 -----> ls /home/git/path you mkdir -p dir name/  and you will see blow <br>

custom  data  gogs  LICENSE  log  public  README.md  README_ZH.md  scripts  templates  <br>  

【Run the installation】<br>

in scripts/mysql.sql  ------> mysql -u root -p < scripts/mysql.sql   (Requires a password) to initialize the database <br>

Then log in to MySQL to create a new user, gogs, and give the user all rights to the database gogs. commond as blow<br>

 $ mysql -u root -p  -------><br> 

（输入密码）-------> <br>

 create user 'gogs'@'localhost' identified by '密码'; -------><br>

 grant all privileges on gogs.* to 'gogs'@'localhost'; -------><br>

 flush privileges;-------><br>

 exit;<br>

Run 【./gogs web】 to get Gogs up and go to http://server IP:3000/ to install it. Fill in the form and submit it.<br>

It should be noted that the 0.6.9.0903 Beta release has a bug that allows administrators not to be added when the<br>

registration is closed so that no users can log in after the installation is complete. So be sure to specify an <br>

administrator account on the installation screen.<br>

【Configuration adjustment】<br>

The configuration file is located in the custom/conf/app.ini of the Gogs directory and is a text file in INI format.<br> 

For detailed configuration explanations and default values, refer to the official documentation. The key configuration<br>

is probably the following.<br>

RUN_USER is git by default, specifying which user Gogs runs<br>

ROOT store root path for all repositories<br>

PROTOCOL Please use http if you use nginx reverse, if you run directly to the outside world<br>

DOMAIN domain name. Affects SSH clone address<br>

ROOT_URL The full root path, which affects the pointing of the links on the page when accessed, and the address of the HTTP clone<br>

HTTP_ADDR listener address. Use nginx to suggest 127.0.0.1, otherwise 0.0.0.0 can also<br>

HTTP_PORT listening port, default 3000<br>

INSTALL_LOCK locks the installation page<br>

Mailer related options<br>

Among them, Mailer can use Mailgun's free e-mail service to fill Mailgun's SMTP configuration into configuration.<br>

【Configure the nginx reverse proxy】<br>

[plz see my another blog about how to setting nginx server](http://git.mydoc.io/)<br>

【Keep the service running】<br>

nohup ./gogs web & <br>

<h3>ok These are the things I want to talk about R U Got it ? have any problems plz contract licslan@sina.com</h3>



