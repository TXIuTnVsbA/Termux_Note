# Termux_折腾笔记

------
## 基本的折腾

### **4. jupyter-notebook的简单配置**

这东西似乎挺牛B，安装完成后，差不多就可以在浏览器上愉快的敲代码(搬砖)了

其实可以直接运行的，然后手机浏览器访问一下就可以了

但是如果你不只是在手机玩耍还需要在电脑上优雅的打开浏览器玩耍的话，那么就该配置一下了

### 生成配置文件:

> jupyter notebook --generate-config

注意: 生成的文件为`~/.jupyter/jupyter_notebook_config.py`

### 修改配置文件:

取消注释然后修改

```
c.NotebookApp.i p= '0.0.0.0'# 这个我也不知道怎么说，反正就是任何Ip都能访问
c.NotebookApp.password = u''  #这个密码晚点再说
c.NotebookApp.open_browser = False # 让这家伙不会一开启就弹出浏览器
c.NotebookApp.port = 8888 # 自定义端口，默认8888
```

这样应该就可以给局域网的人访问了，但是感觉不太安全，还是加个密码吧，于是

### 自动生成密中密码

```
$ jupyter notebook password
Enter password: ***
Verify password: ***
[NotebookPasswordApp] Wrote hashed password to /data/data/com.termux/files/home/.jupyter/jupyter_notebook_config.json
$ cat ~/.jupyter/jupyter_notebook_config.json
{
  "NotebookApp": {
    "password": "sha1:914e...." #密中密码生成，此处省略亿万个字
  }
}
```

### 手动生成密中密码

```
$ ipython
Python 3.7.2 (default, Mar  2 2019, 00:37:44)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.3.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: from notebook.auth import passwd

In [2]: passwd()
Enter password: ***
Verify password: ***
Out[2]: 'sha1:4da...' #密中密码生成，此处省略亿万个字
In [3]: exit()
$
```

### 修改配置文件:

```
c.NotebookApp.password = u'sha1:914e....'  #填下生成的密中密码
```

然后就可以运行`jupyter-notebook`然后访问http://192.168.2.3:8888了(假设192.168.2.3是手机端的ip地址)


恩输入密码后应该就可以愉快的玩耍了



------
## 参考
```
    https://www.cnblogs.com/wu-chao/p/8419889.html
```

