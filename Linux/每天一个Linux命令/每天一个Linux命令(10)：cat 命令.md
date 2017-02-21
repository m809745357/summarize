## 每天一个Linux命令(10)：cat 命令

cat命令的用途是连接文件或标准输入并打印。这个命令常用来显示文件内容，或者将几个文件连接起来显示，或者从标准输入读取内容并显示，它常与重定向符号配合使用。 

> 1.命令格式：

```shell
cat [选项]... [文件]...
```

> 2.命令功能：

cat主要有三大功能：

1. 一次显示整个文件:cat filename
2. 从键盘创建一个文件:cat > filename 只能创建新文件,不能编辑已有文件.
3. 将几个文件合并为一个文件:cat file1 file2 > file

> 3.命令参数：

```shell
# 如果没有指定文件，或者文件为"-"，则从标准输入读取。

  -A, --show-all           # 相当于-vET
  -b, --number-nonblank    # 数字非空输出行，覆盖-n
  -e                       # 相当于-vE
  -E, --show-ends          # 在每行结尾处显示$
  -n, --number             # 编号所有输出线
  -s, --squeeze-blank      # 抑制重复空输出线
  -t                       # 与-vT 等价
  -T, --show-tabs          # 将跳格字符显示为^I
  -u                       # (被忽略)
  -v, --show-nonprinting   # 使用^ 和M- 引用，除了LFD和 TAB 之外
      --help			   # 显示此帮助信息并退出
      --version			   # 显示版本信息并退出

示例：
  cat f - g  先输出f 的内容，然后输出标准输入的内容，最后输出g 的内容。
  cat        将标准输入的内容复制到标准输出。
```

> 4.使用实例：

- 把 log2012.log 的文件内容加上行号后输入 log2013.log 这个文件里`cat -n log2012.log log2013.log `

- 把 log2012.log 和 log2013.log 的文件内容加上行号（空白行不加）之后将内容附加到 log.log 里。

  ```shell
  cat -b log2012.log log2013.log log.log
  ```

- 把 log2012.log 的文件内容加上行号后输入 log.log 这个文件里 

  ```shell
  cat log.log
  cat -n log2012.log > log.log
  cat -n log.log 使用here doc来生成文件
  ```


- 使用here doc来生成文件`cat >log.txt <<EOF`

- tac (反向列示)

  ```shell
  tac log.txt
  ```

  tac 是将 cat 反写过来，所以他的功能就跟 cat 相反， cat 是由第一行到最后一行连续显示在萤幕上，而 tac 则是由最后一行到第一行反向在萤幕上显示出来！