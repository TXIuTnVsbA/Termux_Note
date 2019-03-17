# Termux_折腾笔记

------
## 基本的折腾

### **5. PHP + MySql + phpMyAdmin**

这个感觉好像还挺好玩的，如果配合爬虫，恩，爽阿

search了一下下

```
$ apt search php
Sorting... Done
Full Text Search... Done
doxygen/stable 1.8.15 arm
  A documentation system for C++, C, Java, IDL and PHP

php/stable 7.3.2-1 arm
  Server-side, HTML-embedded scripting language

php-apache/stable 7.3.2-1 arm
  Apache 2.0 Handler module for PHP

php-dev/stable 7.3.2-1 arm
  Development files for php

php-fpm/stable 7.3.2-1 arm
  FastCGI Process Manager for PHP

php-pgsql/stable 7.3.2-1 arm
  PostgreSQL modules for PHP

$ apt search mysql
Sorting... Done
Full Text Search... Done
mariadb/stable 10.3.13 arm
  A drop-in replacement for mysql server

$ 

```

### **安装**

mariadb? php? php-apache? 哇曹？先安装了基本的再说吧

> apt install php mariadb

### **PHP简单配置与测试**

php怎么用来的？管它的呢，我有参考文章我怕谁

```
mkdir ~/www  #新建个专门存放网页的文件夹先
echo "<?php phpinfo();?>" > ~/www/index.php  #写个测试文件先
php -S 0.0.0.0:8080 -t ~/www/  #运行一下，浏览器访问一下，真香
```

会话被占用了？怎么退出？= =默默地Ctrl + C 万能退出大法！

### **mariadb(mysql) 简单配置与测试**

mariadb又是什么鬼，不是mysql吗？管它的呢，我有参考文章我怕谁

Baidu了一圈之后,听说启动之前要运行`mysql_install_db`初始化

```
$ mysql_install_db
Installing MariaDB/MySQL system tables in '/data/data/com.termux/files/usr/var/lib/mysql' ...
OK

To start mysqld at boot time you have to copy
support-files/mysql.server to the right place for your system


PLEASE REMEMBER TO SET A PASSWORD FOR THE MariaDB root USER !
To do so, start the server, then issue the following commands:

'/data/data/com.termux/files/usr/bin/mysqladmin' -u root password 'new-password'
'/data/data/com.termux/files/usr/bin/mysqladmin' -u root -h localhost password 'new-password'

Alternatively you can run:
'/data/data/com.termux/files/usr/bin/mysql_secure_installation'

which will also give you the option of removing the test
databases and anonymous user created by default.  This is
strongly recommended for production servers.

See the MariaDB Knowledgebase at http://mariadb.com/kb or the
MySQL manual for more instructions.

You can start the MariaDB daemon with:
cd '/data/data/com.termux/files/usr' ; /data/data/com.termux/files/usr/bin/mysqld_safe --datadir='/data/data/com.termux/files/usr/var/lib/mysql'

You can test the MariaDB daemon with mysql-test-run.pl
cd '/data/data/com.termux/files/usr/mysql-test' ; perl mysql-test-run.pl

Please report any problems at http://mariadb.org/jira

The latest information about MariaDB is available at http://mariadb.org/.
You can find additional information about the MySQL part at:
http://dev.mysql.com
Consider joining MariaDB's strong and vibrant community:
https://mariadb.org/get-involved/
```

好吧，这是在欺负我不懂英语?

初始化后就该启动服务了

`mysqld` #直接运行会占用这个会话的，这时候就需要会话管理神器`tmux`了

启动后就该改密码了

具体看我一顿骚操作

```
$ tmux #这是个会话管理器，和那个screen差不多，运行后自动新建一个会话
$ mysqld #卡住了对不？ 先Ctrl+B再按D，让tmux把这个会话给收到后台去
$ mysqladmin -u root password 'password' #改密码了喂
$ mysql -uroot -p #启动mysql管理器看看，自己手动输入密码
```

其实还可以用`mysql_secure_installation`(推荐)这个命令来设置相关安全问题

```
#运行
mysql_secure_installation

#输入当前密码, 如果密码没改的话默认是空的, 直接回车即可
Enter current password for root (enter for none):

#更改密码
Set root password? [Y/n] y
New password: 
Re-enter new password:

#其他设置，这个根据个人需求设置
Remove anonymous users? [Y/n] Y                #是否移除匿名用户
Disallow root login remotely? [Y/n] n          #是否不允许root远程登录
Remove test database and access to it? [Y/n] n #是否移除test数据库
Reload privilege tables now? [Y/n] y           #是否重新加载表的权限
```

这会话被收后台了，怎么搞起来？

> Baidu了一圈说
> tmux ls #列出会话,比如会话名称，0，1，2
> tmux a -t 0 #0是会话名称来的

mysqld怎么退出？wdnmd，万能退出大法Ctrl + C 竟然没用 Ctrl + Z 呢？也没用

万能结束大法来了

> killall mysqld #不死也得死，再不行我就关机重启算了

### **phpMyAdmin安装与配置**

wdnmd= =我又不会玩sql，好吧，我还是老老实实用`phpMyAdmin`吧

[`phpMyAdmin`](https://www.phpmyadmin.net/downloads/)去[官网](https://www.phpmyadmin.net/downloads/)下载一个吧,`phpMyAdmin`怎么玩？看操作！

(1) 下载解压安装

```
wget https://files.phpmyadmin.net/phpMyAdmin/4.8.5/phpMyAdmin-4.8.5-all-languages.zip #下载拉
unzip phpMyAdmin-4.8.5-all-languages.zip #解压拉
mv phpMyAdmin-4.8.5-all-languages www/phpMyAdmin #移动拉
```

(2) 配置
> nano www/phpMyAdmin/libraries/config.default.php #配置

修改配置
```
/**
 * MySQL password (only needed with 'config' auth_type)
 *
 * @global string $cfg['Servers'][$i]['password']
 */
$cfg['Servers'][$i]['password'] = 'password'; //mysql密码阿喂

```

(3) 运行与测试

```
tmux #新建会话
mysqld #启动mysql服务,Ctrl + B再按D，收回会话
tmux #新建会话
php -S 0.0.0.0:8080 -t ~/www/ #启动php服务,Ctrl + B再按D，收回会话
```

测试无异常

退出
```
$ tmux ls
0: 1 windows (created Sun Mar 17 22:05:09 2019) [80x23]
1: 1 windows (created Sun Mar 17 22:06:56 2019) [80x23]
$ tmux a -t 1
[exited]
$ killall mysqld
$ tmux a -t 0
[exited]
$

```



------
## 参考
```
    https://www.freebuf.com/geek/170510.html
    https://blog.csdn.net/qq_41490561/article/details/84569204
    https://www.cnblogs.com/kevingrace/p/6496899.html
```

