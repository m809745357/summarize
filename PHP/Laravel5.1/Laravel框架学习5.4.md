## Laravel5.4版本学习-Laravel Homestead

基于Ubuntu16.10和lnmp1.3安装环境下安装Laravel

> 1.使用Laravel Installer 安装

```shell
sudo composer global require "laravel/installer"
sudo laravel new blog
#[RuntimeException]                                                        
#  The Zip PHP extension is not installed. Please install it and try again.  
sudo apt-get install php7.0-zip
# 安装完成之后继续执行sudo laravel new blog
```

> 2.使用Composer Create-Project 安装

```shell
sudo composer create-project --prefer-dist laravel/laravel blog
```

> 3.本地开发服务器

```shell
sudo php artisan serve
# http://localhost:8000
```

> 4.Homestead Laravel安装

在使用 Homestead 之前，需要先安装 [Virtual Box 5.1](https://www.virtualbox.org/wiki/Downloads)、[VMWare](https://www.vmware.com/)或 [Parallels](http://www.parallels.com/products/desktop/) 以及 Vagrant，所有这些软件包都为常用操作系统提供了一个便于使用的可视化安装器。

要使用VMware的话，需要购买 VMware Fusion/Workstation 以及 [VMware Vagrant plug-in](https://www.vagrantup.com/vmware)，尽管不便宜，但是VMware可以提供更好的性能和更好的体验。

要使用Parallels的话，需要安装 [Parallels Vagrant plug-in](https://github.com/Parallels/vagrant-parallels)，这是免费的。

```shell
# 安装 Homestead Vagrant 盒子
sudo apt-get install vagrant
sudo vagrant box add laravel/homestead

# 通过 GitHub 安装 Homestead
cd ~
sudo git clone https://github.com/laravel/homestead.git Homestead
cd Homestead
sudo bash init.sh

# 修改站点信息或者同步文件夹信息
sudo vim ~/.homestead/Homestead.ymal

# 修改vagrant版本 
sudo vim Vagrantfile 
# Vagrant.require_version '<= 1.9.0'

# 修改homestead限制
sudo vim /home/shenyifei/Homestead/scripts/homestead.rb 
# config.vm.box_version = settings["version"] ||= "<= 1.1.0"

# 创建ssh
sudo ssh-keygen -t rsa -f /home/shenyifei/.ssh/id_rsa -C "809745357@qq.com"

# 编辑
sudo vim /etc/hosts
# 192.168.10.10 homestead.app

# vagrant 开启 关机 重启
sudo vagrant up
sudo vagrant halt
sudo vagrant reload

# vagrant 销毁
sudo vagrant destroy --force
```



