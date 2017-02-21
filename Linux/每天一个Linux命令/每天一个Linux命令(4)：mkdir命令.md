## 每天一个 Linux 命令(4)：mkdir命令

linux mkdir 命令用来创建指定的名称的目录，要求创建目录的用户在当前目录中具有写权限，并且指定的目录名不能是当前目录中已有的目录。   

> 1.命令格式

```shell
mkdir [选项] 目录...
```

> 2.命令功能

通过 mkdir 命令可以实现在指定位置创建以 DirName(指定的文件名)命名的文件夹或目录。要创建文件夹或目录的用户必须对所创建的文件夹的父文件夹具有写权限。并且，所创建的文件夹(目录)不能与其父目录(即父文件夹)中的文件名重名，即同一个目录下不能有同名的(区分大小写)。

> 3.命令参数

```shell
  -m, --mode=MODE   	# 设置文件模式（如chmod中），而不是a = rwx - umask
  -p, --parents     	# 没有错误，如果存在，根据需要创建父目录
  -v, --verbose     	# 为每个创建的目录打印一条消息
  -Z                	# 将每个创建的目录的SELinux安全上下文设置为默认类型
      --context[=CTX]  	# 如-Z，或者如果指定了CTX，则将SELinux或SMACK安全上下文设置为CTX
      --help			# 显示此帮助信息并退出
      --version		 	# 显示版本信息并退出
```

> 4.命令实例

1. 创建一个空目录``` mkdir test1```

2. 递归创建多个目录```mkdir -p test2/test22```

3. 创建权限为777的目录```mkdir -m 777 test3```

4. 创建新目录都显示信息```mkdir -v test4```

5. 一个命令创建项目的目录结构

   ```shell
   mkdir -vp scf/{lib/,bin/,doc/{info,product},logs/{info,product},service/deploy/{info,product}}
   mkdir: 已创建目录 “scf”
   mkdir: 已创建目录 “scf/lib”
   mkdir: 已创建目录 “scf/bin”
   mkdir: 已创建目录 “scf/doc”
   mkdir: 已创建目录 “scf/doc/info”
   mkdir: 已创建目录 “scf/doc/product”
   mkdir: 已创建目录 “scf/logs”
   mkdir: 已创建目录 “scf/logs/info”
   mkdir: 已创建目录 “scf/logs/product”
   mkdir: 已创建目录 “scf/service”
   mkdir: 已创建目录 “scf/service/deploy”
   mkdir: 已创建目录 “scf/service/deploy/info”
   mkdir: 已创建目录 “scf/service/deploy/product”
   tree scf/
   scf/
   |-- bin
   |-- doc
   |   |-- info
   |   `-- product
   |-- lib
   |-- logs
   |   |-- info
   |   `-- product
   `-- service
      `-- deploy
     	    	|-- info
           	`-- product
   12 directories, 0 files
   ```