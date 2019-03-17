# Termux_折腾笔记

------
## 基本的折腾

### 1. apt & pkg

> Termux除了支持`apt`命令外,还在此基础上封装了`pkg`命令,`pkg`命令向下兼容`apt`命令.`apt`命令大家应该都比较熟悉了,这里直接简单的介绍下`pkg`命令:

```
pkg search <query>              搜索包
pkg install <package>           安装包
pkg uninstall <package>         卸载包
pkg reinstall <package>         重新安装包
pkg update                      更新源
pkg upgrade                     升级软件包
pkg list-all                    列出可供安装的所有包
pkg list-installed              列出已经安装的包
pkg shoe <package>              显示某个包的详细信息
pkg files <package>             显示某个包的相关文件夹路径
```

不管干什么，拿到手就是
```
apt update
apt upgrade
```

然后安装基本工具:
```
apt update
apt install vim curl wget git unzip unrar
```


如果慢的话可以

##### 更改源:

```
设置默认编辑器:
    export EDITOR=vi
编辑源文件:
    apt edit-sources
替换:
    将原来的https://termux.net
    替换为http://mirrors.tuna.tsinghua.edu.cn/termux
更新:
    apt update
```

### 2. ssh

手机打命令应该很痛苦吧？搞定了这个应该就解放了(或者你手机连接键盘我也不拦着你，但是始终得连接电脑的),

于是,

手机端安装ssh:
```
pkg install openssh
```

拷贝电脑端生成的Key:
```
ubuntu:-> ssh-keygen -t rsa
win:-> 参考git
```

> 最后，电脑端会生成`id_rsa`, `id_rsa.pub`
>
> 然后,电脑端拷贝公钥id_rsa.pub到手机端Termux的key目录件中,重命名为`authorized_keys`

> Linux(不管是Pc还是Termux)的key目录是`~/.ssh/`
>
> Win的话,参考git，看你个人能力的时候到了

> 怎么Copy就需要在Termux建立一个链接文件夹了，具体命令:
> 
> ```
> termux-setup-storage
> ```
> 
> 然后就会多出了一些目录,我认为贴出了这个你应该会懂的
> 
> ```
> $ ls
> storage
> $ ls -l storage/
> total 0
> lrwxrwxrwx    1 u0_a161  u0_a161         24 Mar 17 17:30 dcim -> /storage/emulated/0/DCIM
> lrwxrwxrwx    1 u0_a161  u0_a161         28 Mar 17 17:30 downloads -> /storage/emulated/0/Download
> lrwxrwxrwx    1 u0_a161  u0_a161         48 Mar 17 17:30 external-1 -> /storage/72AD-2013/Android/data/com.termux/files
> lrwxrwxrwx    1 u0_a161  u0_a161         26 Mar 17 17:30 movies -> /storage/emulated/0/Movies
> lrwxrwxrwx    1 u0_a161  u0_a161         25 Mar 17 17:30 music -> /storage/emulated/0/Music
> lrwxrwxrwx    1 u0_a161  u0_a161         28 Mar 17 17:30 pictures -> /storage/emulated/0/Pictures
> lrwxrwxrwx    1 u0_a161  u0_a161         19 Mar 17 17:30 shared -> /storage/emulated/0
> $
> ```
> 

最后,
手机端开启服务:
```
ifconfig #这只是给你看看你现在的ip是多少而已
sshd #开启服务啦
netstat -anp|grep sshd #给你看看绑定哪个端口而已拉，一般是8022
```
电脑端连接:
```
 ubuntu:-> ssh 192.168.2.3 -p 8022 #假设192.168.2.3是手机端的Ip
 
 Win:-> 具体参考putty,用PUTTYGEN导入id_rsa文件生成ppk为后戳的私密文件,
        再用PAGEANT导入ppk文件,创建会话连接Termux,无需输入用户名和密码，直接回车即可
```

------
## 参考
```
    https://www.freebuf.com/geek/170510.html
```

