## Ubuntu16.10系统软件安装和主题美化

#### Shadowsocks

> 通过PPA源安装，仅支持Ubuntu 14.04或更高版本。

```shell
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
# 图形版比较简单，自己配置，加密方式选择aes-256-cfb
```

> 通过pip安装

```shell
sudo apt-get install python-pip
sudo pip install shadowsocks
# 直接输入命令运行 终端输入 sslocal -help 可以看到帮助文件
sslocal -help
# -s后面跟你的服务器ip ， -p后面跟你远程端口号（默认8388） ，-k后面跟你的密码（写在双引号之间），其他的用默认选项就好
sslocal -s 1.1.1.1 -p 8388 -k "your passwd" -b 127.0.0.1 -l 1080 
# 在你的~目录下新建一个.json文件
touch ss.json ~/
{
    "server":"1.1.1.1",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"your passwd",
    "timeout":300,
    "method":"aes-256-cfb"
}
sslocal -c ~/ss.json
```

> kill1080进程

```shell
netstat -tunlp|grep 1080
tcp        0      0 0.0.0.0:1080            0.0.0.0:*               LISTEN      2665/EmbedThunderMa
kill 2665 # EmbedThunderMa 是迅雷进程，需要去关闭他设置成ETM随前段关闭而关闭，若是其他端口直接kill
```



#### Proxychains

> 修改最后一行为：将socks4 127.0.0.1 9095改为 socks5  127.0.0.1 1080 //1080改为你自己的端口

```shell
sudo apt-get install proxychains
sudo vim /etc/proxychains.conf 
```

### Typora

> 很不错的一个markdown工具

```shell
# optional, but recommended
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
# add Typora's repository
sudo add-apt-repository 'deb https://typora.io ./linux/'
sudo apt-get update
# install typora
sudo apt-get install typora
```

### Google-Chrome

> 下载[google-chrome-stable](http://www.ubuntuchrome.com/downubuntuchrome) 

```shell
dpkg -i google-chrome-stable_current_amd64.deb
```

> 下载[SwitchyOmega](https://github.com/FelisCatus/SwitchyOmega/releases)，然后打开chrome安装该扩展程序

> AutoProxy: https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt

### Dropbox

> 下载[dropbox](https://www.dropbox.com) 首次打开使用命令打开，利用代理下载相关信息

```shell
proxychains dropbox start -i
```

### Indicator-multiload

```shell
sudo apt-get install indicator-multiload
```

