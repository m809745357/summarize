## Ubuntu16.10安装Xware Desktop

> **安装必备的软件**

```shell
sudo apt-get install git build-essential devscripts
```

> **下载源码**

```shell
sudo git clone git://github.com/Xinkai/XwareDesktop.git # 这会在当前目录下生成一个名为XwareDesktop的子目录。
```

> **切换到源代码目录XwareDesktop**。

```shell
cd XwareDesktop
```

> **列出缺失的编译依赖**

```shell
dpkg-checkbuilddeps
```

> **安装缺失的编译依赖**

```shell
sudo apt-get install <复制粘贴:上一步列出的缺失的编译依赖>
```

> **制作安装包**

```shell
dpkg-buildpackage
```

> **安装**

```shell
sudo gdebi xware-desktop_xxx.deb
```

> 原文链接

https://github.com/Xinkai/XwareDesktop/wiki