## Ubuntu16.10设置开机动画

> 开机动画文件夹：Ubuntu16.10的开机动画在/usr/share/plymouth/themes文件夹

> Ubuntu开机动画下载（http://packages.ubuntu.com/trusty/all/plymouth-theme-ubuntu-gnome-text/download）

```shell
sudo apt-get install plymouth-theme* # 使用命令下载主题，需要切换到bash
```

> 选择开机动画

```shell
sudo update-alternatives --config default.plymouthupdate-alternatives
```

> 命令详见Ubuntu中update-alternatives命令（版本切换）：[http://www.linuxdiyf.com/linux/13855.html](http://www.linuxdiyf.com/linux/13855.html)

```shell
sudo update-initramfs  -u # 使配置生效
```

> 不小心安装了Xubuntu-desktop，卸载后，登录界面还是Xubuntu-desktop的界面

```shell
sudo dpkg-reconfigure lightdm
sudo vim /etc/lightdm/lightdm.conf
# 输入以下代码
[SeatDefaults] 
greeter-session=unity-greeter
```

