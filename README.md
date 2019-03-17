# Termux_折腾笔记

------
## **目录**

> 基本的折腾

[1. apt & pkg][1]

[----------------更改apt源][2]

[2. ssh][3]

[3. Python (一小部分)][4]

[----------------安装Python与一些工具][5]

[----------------更改PyPi源][6]

[----------------安装部分Python模块][7]

[--------------------------------安装BeautifulSoup,requests][8]

[--------------------------------安装lxml模块][9]

[--------------------------------安装scrapy模块][10]

[--------------------------------安装numpy模块][11]

[--------------------------------安装matplotlib,pandas,jupyter][12]

[4. jupyter-notebook (简单搭建配置)][13]

[5. PHP + MySql + phpMyAdmin (简单搭建配置)][14]



------
## 参考汇总
```
    https://www.freebuf.com/geek/170510.html
    https://www.zhihu.com/question/63482921/answer/209835936
    https://www.jianshu.com/p/4deba3fad266
    https://lug.ustc.edu.cn/wiki/mirrors/help/pypi
    https://github.com/myfreess/Mytermuxdoc
    https://www.cnblogs.com/yangxiaolan/p/5778305.html
    https://www.cnblogs.com/wu-chao/p/8419889.html
    https://blog.csdn.net/qq_41490561/article/details/84569204
    https://www.cnblogs.com/kevingrace/p/6496899.html
```


  [1]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.1.md#1-apt--pkg
  [2]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.1.md#%E6%9B%B4%E6%94%B9%E6%BA%90
  [3]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.1.md#2-ssh
  [4]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#3python
  [5]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#%E5%AE%89%E8%A3%85%E5%9F%BA%E6%9C%AC%E5%B7%A5%E5%85%B7
  [6]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#%E6%9B%B4%E6%94%B9pypi%E6%BA%90%E6%98%AF%E8%BF%99%E4%B9%88%E5%8F%AB%E7%9A%84%E5%90%A7
  [7]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#%E5%AE%89%E8%A3%85python%E6%A8%A1%E5%9D%97
  [8]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#1-%E5%AE%89%E8%A3%85beautifulsouprequests
  [9]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#2-%E5%AE%89%E8%A3%85lxml%E6%A8%A1%E5%9D%97
  [10]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#3-%E5%AE%89%E8%A3%85scrapy%E6%A8%A1%E5%9D%97%E5%BF%85%E9%A1%BB%E5%85%88%E5%AE%89%E8%A3%85lxml%E6%89%8D%E8%A1%8C
  [11]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#4-%E5%AE%89%E8%A3%85numpy%E6%A8%A1%E5%9D%97-%E8%BF%99%E4%B8%AA%E6%A8%A1%E5%9D%97%E7%9A%84%E5%AE%89%E8%A3%85%E8%B4%BC%E6%81%B6%E5%BF%83
  [12]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.2.md#5-%E5%AE%89%E8%A3%85matplotlib-pandas-jupyter
  [13]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.3.md#4-jupyter-notebook%E7%9A%84%E7%AE%80%E5%8D%95%E9%85%8D%E7%BD%AE
  [14]: https://github.com/TXIuTnVsbA/Termux_Note/blob/master/%E5%9F%BA%E6%9C%AC%E7%9A%84%E6%8A%98%E8%85%BE_Pt.4.md#5-php--mysql--phpmyadmin
