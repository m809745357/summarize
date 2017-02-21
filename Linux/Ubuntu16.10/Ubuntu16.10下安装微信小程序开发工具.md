## Ubuntu16.10下安装微信小程序开发工具

> 安装前的准备

- 首先[下载](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/download.html)windows版本的微信web开发工具。
- [下载](https://nwjs.io/)nwjs NORMAL版本。
- 拷贝window系统下安装的微信web开发者工具文件夹中的package.nw、icon.ico、* 微信web开发者工具.exe到nwjs的解压目录下面。

> 开始安装进入nwjs目录

```shell
sudo ./nw # 运行，运行之后如果报错，需要执行以下命令。
# 进入package.nw目录下执行一下命令
sudo sed -i 's/\.\/Create\/create\.js/\.\/create\/create\.js/ig' app/dist/components/ContainController.js
sudo sed -i 's/\.\/main\.js/\.\/Main\.js/ig' app/dist/components/ContainController.js
sudo sed -i 's/\.\/webview\/Picker/\.\/webview\/picker/ig' app/dist/components/simulator/controller.js
sudo sed -i 's/\.\/webview\/ActionSheet\.js/\.\/webview\/actionSheet\.js/ig' app/dist/components/simulator/controller.js
sudo sed -i 's/appServiceConfig\.js/appserviceConfig\.js/ig' app/dist/common/assdk/NetworkSdk.js
```

> 参考资料

* http://www.07net01.com/2016/12/1760918.html
* http://blog.csdn.net/ghostyusheng/article/details/54312550