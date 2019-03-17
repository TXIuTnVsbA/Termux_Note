# Termux_折腾笔记

------
## 基本的折腾

### **3.Python**

由于我就只会玩Python(惭愧了), 所以就。。。。。

### 安装基本工具

> apt install tmux tsu wget git zip neofetch clang make cmake curl 

### 安装Python

注意这里默认是python3

> apt install python python-dev python2 python2-dev

### 更改Pypi源(是这么叫的吧？)

编辑`~/.pip/pip.conf`,没有就自己创建一个

更改内容:

```
[global]
index-url = https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple
format = columns
```

### 安装Python模块

安装之前，还是先升级以下pip吧:

> pip install --upgrade pip

#### (1) 安装BeautifulSoup,requests

> pip install BeautifulSoup4 requests

#### (2) 安装lxml模块

为避免lxml安装失败，先安装一堆我也不知道有没有用的东西

> apt install libxml2 libxml2-dev libxslt libxslt-dev libcrypt libcrypt-dev openssl openssl-dev libffi libffi-dev

然后再安装模块，就差不多了，一般是可以安装的(除非你运气差)

> pip install lxml

这里安装有点慢，请耐心等待

#### (3) 安装scrapy模块（必须先安装lxml才行）

> pip install scrapy

#### (4) 安装numpy模块 (这个模块的安装贼恶心)

又要安装一堆我不懂的东西了

> apt install clang python python-dev fftw libzmq libzmq-dev freetype freetype-dev libpng libpng-dev pkg-config

直接下载并执行别人搞定的脚本

> curl -L https://its-pointless.github.io/setup-pointless-repo.sh | sh

然后执行下一个命令即可，那个男人说，会自动安装你要的模块的

> pkg install scipy

一般是能安装的，要是不能，我也没办法，我是小白，我写给我自己看的

#### (5) 安装matplotlib pandas jupyter

= =这个东西嘛，

我mtk x20 + 3g RAM，安装起来有点慢

我高通410 + 2g RAM，直接就卡住了，我相信它会安装完成的，只是时间问题而已

> LDFLAGS=" -lm -lcompiler_rt" pip install matplotlib pandas jupyter

------
## 参考
```
    https://www.freebuf.com/geek/170510.html
    https://www.zhihu.com/question/63482921/answer/209835936
    https://www.jianshu.com/p/4deba3fad266
    https://lug.ustc.edu.cn/wiki/mirrors/help/pypi
    https://github.com/myfreess/Mytermuxdoc
```

