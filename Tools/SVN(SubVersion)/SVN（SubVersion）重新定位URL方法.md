## SVN（SubVersion）重新定位URL方法

> 如果更换了SVN服务器，就需要重新定位，指向新的SVN URL。

```shell
cd /projects/jiushu.huishuoit.com
# 查看原svn路径方法：svn info
svn info
路径: .
URL: https://218.75.69.250:443/svn/Projects/jiushu/trunk
版本库根: https://218.75.69.250:443/svn/Projects
版本库 UUID: 18ba064a-3021-384c-a4e9-358e4660050c
版本: 4586
节点种类: 目录
调度: 正常
最后修改的作者: php-ws
最后修改的版本: 4586
最后修改的时间: 2016-12-28 17:38:24 +0800 (三, 2016-12-28)
# 重新定位命令：svn switch --relocate 原svn地址 新svn地址
svn switch --relocate https://218.75.69.250:443/svn/Projects/jiushu/trunk https://223.93.134.173:443/svn/Projects/jiushu/trunk
```

