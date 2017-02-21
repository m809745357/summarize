# laravel 框架学习5.1

http://www.golaravel.com/laravel/docs/5.1/

**PHP >= 5.5.9 - OpenSSL PHP 扩展 - PDO PHP 扩展 - Mbstring PHP 扩展 - Tokenizer PHP 扩展 **

#### Laravel 利用Composer来管理其自身的依赖包

> ubuntu16.10安装Composer工具

```shell
sudo apt-get update
sudo apt-get install composer
# 给composer 777权限
sudo chmod -R 777 ~/.composer/
```

> Windows安装Composer工具

下载并安装[Composer-Setup.exe](https://getcomposer.org/Composer-Setup.exe) 配置全局的环境变量

> Composer配置中国镜像

```shell
# 系统全局配置： 即将配置信息添加到 Composer 的全局配置文件 config.json 中。
composer config -g repo.packagist composer https://packagist.phpcomposer.com
# 单个项目配置： 将配置信息添加到某个项目的 composer.json 文件中。
composer config repo.packagist composer https://packagist.phpcomposer.com
```

> 提示：不要忘了经常执行 ```composer selfupdate```以保持 Composer 一直是最新版本哦！

#### 通过 Laravel 安装工具安装 Laravel

> 首先，使用 Composer 下载 Laravel 安装包：

```shell
composer global require "laravel/installer"
```

> 设置全局lararvl安装包

```shell
sudo ln -s ~/.composer/vendor/bin/laravel /usr/bin/laravel
```

> 两种方式安装laravel

```shell
# 使用Laravel安装包安装一个名称为blog的项目
laravel new blog
# 使用Composer工具创建一个laravel5.1.0版本项目
composer create-project laravel/laravel:v5.1.0 --prefer-dist
# 给该项目的bootstrap/cache和storage文件目录权限
sudo chmod -R 777 storage bootstrap/cache
```

#### 安装可能遇到的问题

##### laravel/framework v5.3.9 requires ext-mbstring

```shell
# php没有开启mbstring
sudo apt-get install php-mbstring
```

##### laravel/framework v5.3.9 requires ext-dom

```shell
# php没有开启dom
sudo apt-get install php-dom
```

##### The only supported ciphers are AES-128-CBC and AES-256-CBC with the correct key lengths.

```shell
php artisan key:generate
Application key [ebjMlFCTA1F4CK76BGoMLCo5AnrkCRj2] set successfully.
```

#### 配置站点

需要将站点配置在项目文件的public下。跟多请看[laravel5.1手册](http://www.golaravel.com/laravel/docs/5.1/)