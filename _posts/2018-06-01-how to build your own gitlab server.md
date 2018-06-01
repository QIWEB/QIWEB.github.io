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

ok let`s get to the right point 

next i will intorduce how to use git commod <br>

of course it`s sort of base commod such as you can download code or file from your server<br>

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

6.Keep the service running;<br>

Note that by default you have already installed MySQL server (or MariaDB) and nginx. If not, <br>

find out how to install and configure these dependencies. Of course, you can also use the SQLite database.<br>

to be continued。。。
