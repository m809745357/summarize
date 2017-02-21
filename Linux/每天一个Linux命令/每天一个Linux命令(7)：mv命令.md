## 每天一个Linux命令(7)：mv命令

mv命令是move的缩写，可以用来移动文件或者将文件改名（move（rename）files），是Linux系统下常用的命令，经常用来备份文件或者目录。

> 1.命令格式

```shell
mv [选项]... [-T] 源文件 目标文件
mv [选项]... 源文件... 目录
mv [选项]... -t 目录 源文件...
```

> 2.命令功能

视mv命令中第二个参数类型的不同（是目标文件还是目标目录），mv命令将文件重命名或将其移至一个新的目录中。当第二个参数类型是文件时，mv命令完成文件重命名，此时，源文件只能有一个（也可以是源目录名），它将所给的源文件或目录重命名为给定的目标文件名。当第二个参数是已存在的目录名称时，源文件或目录参数可以有多个，mv命令将各参数指定的源文件均移至目标目录中。在跨文件系统移动文件时，mv先拷贝，再将原有文件删除，而链至该文件的链接也将丢失。

> 3.命令参数

```shell
      --backup[=CONTROL]       # 为每个已存在的目标文件创建备份
  -b                           # 类似--backup 但不接受参数
  -f, --force                  # 覆盖前不询问
  -i, --interactive            # 覆盖前询问
  -n, --no-clobber             # 不覆盖已存在文件如果您指定了-i、-f、-n 中的多个，仅最后一个生效。
      --strip-trailing-slashes # 去掉每个源文件参数尾部的斜线
  -S, --suffix=SUFFIX		   # 替换常用的备份文件后缀
  -t, --target-directory=DIRECTORY  # 将所有SOURCE参数移动到DIRECTORY
  -T, --no-target-directory    # 将DEST视为正常文件
  -u, --update                 # 仅当SOURCE文件比目标文件更新或目标文件丢失时移动
  -v, --verbose                # 解释正在做什么
  -Z, --context                # 将目标文件的SELinux安全上下文设置为默认类型
      --help		# 显示此帮助信息并退出
      --version		# 显示版本信息并退出

备份后缀为“~”，除非使用--suffix或SIMPLE_BACKUP_SUFFIX设置。
可以通过--backup选项或通过选择版本控制方法
VERSION_CONTROL环境变量。 这里是值：

  none, off       不进行备份(即使使用了--backup 选项)
  numbered, t     备份文件加上数字进行排序
  existing, nil   若有数字的备份文件已经存在则使用数字，否则使用普通方式备份
  simple, never   永远使用普通方式备份

```

> 4.命令实例

- 文件改名`mv test.log test1.txt`
- 移动文件`mv test1.txt test3`
  - 将文件log1.txt,log2.txt,log3.txt移动到目录test3中 `mv log1.txt log2.txt log3.txt test3` `mv -t /opt/soft/test/test4/ log1.txt log2.txt log3.txt `
- 将文件file1改名为file2，如果file2已经存在，则询问是否覆盖`mv -i log1.txt log2.txt`
- 将文件file1改名为file2，即使file2存在，也是直接覆盖掉`mv -f log3.txt log2.txt`
- 目录的移动`mv dir1 dir2 
- 移动当前文件夹下的所有文件到上一级目录`mv * ../`
- 把当前目录的一个子目录里的文件移动到另一个子目录里`mv test3/*.txt test5`
- 文件被覆盖前做简单备份，前面加参数-b`mv log1.txt -b log2.txt`