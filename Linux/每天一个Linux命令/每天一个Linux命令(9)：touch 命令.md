## 每天一个linux命令(9)：touch 命令

linux的touch命令不常用，一般在使用make的时候可能会用到，用来修改文件时间戳，或者新建一个不存在的文件。

将每个FILE的访问和修改时间更新为当前时间。不存在的FILE参数将创建为空，除非-c或-h。FILE参数字符串 - 被特别处理，并导致触摸更改与标准输出关联的文件的时间。

> 1.命令格式

```shell
touch [选项]... 文件...
```

> 2.命令参数

```shell
  -a				# 只更改访问时间
  -c, --no-create	# 不创建任何文件
  -d, --date=字符串  # 使用指定字符串表示时间而非当前时间
  -f			(忽略)
  -h, --no-dereference	# 会影响符号链接本身，而非符号链接所指示的目的地(当系统支持更改符号链接的所有者时，此选项才有用)
  -m			    	# 只更改修改时间
  -r, --reference=FILE  # 使用此文件的时间而不是当前时间
  -t STAMP              # 使用[[CC] YY] MMDDhhmm [.ss]而不是当前时间
      --time=WORD       # 更改指定的时间：WORD是access，atime或use：相当于-a WORD是modify或mtime：等效于-m
      --help			# 显示此帮助信息并退出
      --version			# 显示版本信息并退出

请注意，-d 和-t 选项可接受不同的时间/日期格式。

```

> 3.命令功能

touch命令参数可更改文档或目录的日期时间，包括存取时间和更改时间。 

> 4.使用范例

- 创建不存在的文件`touch log2012.log log2013.log`
- 更新log.log的时间和log2012.log时间戳相同`touch -r log.log log2012.log`
- 设定文件的时间戳`touch -t 201211142234.50 log.log`

-t  time 使用指定的时间值 time 作为指定文件相应时间戳记的新值．此处的 time规定为如下形式的十进制数:  [[CC]YY]MMDDhhmm[.SS]这里，CC为年数中的前两位，即”世纪数”；YY为年数的后两位，即某世纪中的年数．如果不给出CC的值，则touch   将把年数CCYY限定在1969--2068之内．MM为月数，DD为天将把年数CCYY限定在1969--2068之内．MM为月数，DD为天数，hh 为小时数(几点)，mm为分钟数，SS为秒数．此处秒的设定范围是0--61，这样可以处理闰秒．这些数字组成的时间是环境变量TZ指定的时区中的一个时 间．由于系统的限制，早于1970年1月1日的时间是错误的。