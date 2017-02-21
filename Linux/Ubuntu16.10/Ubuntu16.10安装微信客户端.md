## Ubuntu16.10安装微信客户端

> 安装nodejs,npm,electronic-wechat源码编译安装

```shell
# 由于ubuntu系统本身自带的nodejs会和下载下来npm冲突，这边使用在网站上直接下载nodejs源码。
cd /usr/local/
sudo wget https://nodejs.org/dist/v6.9.4/node-v6.9.4-linux-x64.tar.xz
xz -d node-v6.9.4-linux-x64.tar.xz
tar -zxvf node-v6.9.4-linux-x64.tar # 解包
sudo mv node-v6.9.4-linux-x64.tar node # 重命名
# 设置全局变量让系统支持全局的node和npm，可能需要删除原有的node。
ln -s /usr/local/node/bin/node /usr/bin/node
ln -s /usr/local/node/bin/npm /usr/bin/npm
# 进入软件安装位置，并安装
cd /opt/
sudo git clone https://github.com/geeeeeeeeek/electronic-wechat.git
cd electronic-wechat
sudo npm install
# 启动程序
sudo npm start
```

> 直接下载应用(二进制包)electronic-wechat-linux-x64.tar.gz

```shell
cd /opt/
# 下载应用
sudo wget https://github.com/geeeeeeeeek/electronic-wechat/releases/download/v1.4.0/linux-x64.tar.gz
# 解压并进入资源下载目录
tar -zxvf electronic-wechat-linux-x64.tar.gz && sudo mv electronic-wechat-linux-x64 electronic-wechat && cd electronic-wechat/resources
# 下载程序icon
sudo wget https://raw.githubusercontent.com/geeeeeeeeek/electronic-wechat/master/assets/icon.png -O electronic-wechat.png
# 添加桌面启动
sudo vim /usr/share/applications/electronic-wechat.desktop
# 输入以下代码
[Desktop Entry]
Name=Electronic Wechat
Name[zh_CN]=微信电脑版
Name[zh_TW]=微信电脑版
Exec=/opt/electronic-wechat/electronic-wechat
Icon=/opt/electronic-wechat/resources/electronic-wechat.png
Terminal=false
X-MultipleArgs=false
Type=Application
Encoding=UTF-8
Categories=Application;Utility;Network;InstantMessaging;
StartupNotify=false
```

> 编译环境

其实我们做好编译安装后还可以打包成二进制包，但是我这边失败，一直没有进度

```shell
sudo npm run build:linux # 打包后，会在目录下面生成一个dist文件，这个文件内容和直接下载二进制包内容一致。
```

参考原文连接：https://github.com/gatieme/AderXCoding/tree/master/system/tools/electronic_wechat