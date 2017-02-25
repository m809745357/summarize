## Express 应用生成器

### 通过应用生成器工具express可以快速创建一个应用的骨架

#### 通过如下命令安装：

```shell
npm install express-generator -g
```

#### -h 选项可以列出所有可用的命令行选项：

```shell
express -h

  Usage: express [options] [dir]

  Options:

    -h, --help           output usage information
        --version        output the version number
    -e, --ejs            add ejs engine support
        --pug            add pug engine support
        --hbs            add handlebars engine support
    -H, --hogan          add hogan.js engine support
    -v, --view <engine>  add view <engine> support (ejs|hbs|hjs|jade|pug|twig|vash) (defaults to jade)
    -c, --css <engine>   add stylesheet <engine> support (less|stylus|compass|sass) (defaults to plain css)
        --git            add .gitignore
    -f, --force          force on non-empty directory

```

#### 例如，下面的示例就是在当前工作目录下面创建一个命名为myapp的应用。

```shell
express myapp
```

#### 然后安装所有依赖包

```shell
cd myapp
npm install
```

#### 启动这个应用（MacOS或Linux平台）

```shell
DEBUG=myapp npm start
```

#### Windows平台使用如下命令

```shell
set DEBUG=myapp & npm start
```

#### 然后在浏览器中打开 `http://localhost:3000/` 网址就可以看到这个应用了。

### 查看端口使用情况，使用netstat命令。

查###看已经连接的服务端口（ESTABLISHED)

```shell
netstat -a
```

#### 查看所有的服务端口（LISTEN，ESTABLISHED）

```shell
netstat -ap
```

#### 查看3000端口，则可以结合grep命令：

```sehll
netstat -ap | grep 3000
```

#### 如查看3000端口，则在终端中输入：

```sehll
lsof -i:3000
```

#### 若要停止使用这个端口的程序，使用kill +对应的pid即可

```shell
kill -9 3000
```

#### 使用supervisor调试express

```shell
sudo npm install -g supervisor
sudo ln -s /usr/local/node/bin/supervisor /usr/bin/supervisor
supervisor ./bin/www
```

