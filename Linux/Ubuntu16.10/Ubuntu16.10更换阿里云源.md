## ubuntu16.10更换阿里云源

> 运行命令更新阿里云源

```shell
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak # 备份
sudo sed -i 's/http:\/\/archive.ubuntu.com\/ubuntu\//http:\/\/cn.archive.ubuntu.com\/ubuntu\//g' /etc/apt/sources.list.com\/ubuntu\//g
```

> 手动更改阿里云源

```shell
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak # 备份
sudo vim /etc/apt/sources.list # 修改成阿里云源
sudo apt-get update # 更新列表
```

> 阿里云源

deb http://cn.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

