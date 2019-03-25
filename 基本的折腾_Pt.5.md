# Termux_折腾笔记

------
## 基本的折腾

### **6. 搭建Aria2服务**

### **7. 搭建Hexo博客**

### **8. Termux插件**

连接: [Addos][1]

别的插件就不说了(= =我没玩过)，就说说这个Termux:Boot插件，这个插件牛B了，可以让termux自启

不管怎么说，先安装Termux-Api先:

```pkg install termux-api```

再安装[Termux:Boot][2]插件，安装后打开这个App，允许自启的权限

再创建`~/.termux/boot/` 目录，然后就可以放脚本了，比如，我的脚本`~/.termux/boot/start-sshd`:

```
termux-wake-lock
sshd
```


------
## 参考
```
    https://www.freebuf.com/geek/170510.html
```


  [1]: https://wiki.termux.com/wiki/Addons
  [2]: https://wiki.termux.com/wiki/Termux:Boot
