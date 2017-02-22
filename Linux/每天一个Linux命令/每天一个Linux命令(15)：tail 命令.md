## 每天一个Linux命令(15)：tail 命令

tail 命令从指定点开始将文件写到标准输出.使用tail命令的-f选项可以方便的查阅正在改变的日志文件,tail -f filename会把filename里最尾部的内容显示在屏幕上,并且不但刷新,使你看到最新的文件内容.

> 1.命令格式

```shell
tail [选项]... [文件]...
```

> 2.命令功能

用于显示指定文件末尾内容，不指定文件时，作为输入信息进行处理。常用查看日志文件。

> 3.命令参数

```shell
  -c, --bytes=[+]NUM       # 输出最后NUM个字节; 或使用-c + NUM从每个文件的字节NUM开始输出
  -f, --follow[={name|descriptor}]
                           # 随着文件增长输出附加数据;缺少选项参数意味着“描述符”
  -F                       # 与--follow = name --retry相同
  -n, --lines=[+]NUM       # 输出最后NUM行，而不是最后10行;或使用-n + NUM从行NUM开始输出
      --max-unchanged-stats=N
                           # 使用--follow = name，重新打开一个FILE，它在N（默认为5）迭代后没有改变大小，以查看它是否已被取消链接或重命名（这是旋转日志文件的通常情况）;使用inotify，此选项很少有用
      --pid=PID            # 与-f，终止后的进程ID，PID死
  -q, --quiet, --silent    # 从不输出头文件名
      --retry              # 如果文件不可访问，请继续尝试打开文件
  -s, --sleep-interval=N   # 使用-f，在迭代之间休眠大约N秒（默认为1.0）;使用inotify和-pid = P，每N秒至少检查一次进程P一次
  -v, --verbose            # 总是输出头文件名
  -z, --zero-terminated    # 行分隔符是NUL，而不是换行符
      --help			   # 显示此帮助信息并退出
      --version			   # 显示版本信息并退出
```

> 4.使用实例

1. 显示文件末尾内容`tail -n 5 log2014.log`
2. 循环查看文件内容`tail -f test.log`
3. 从第5行开始显示文件`cat log2014.log`