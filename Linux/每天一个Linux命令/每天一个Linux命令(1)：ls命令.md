## 每天一个Linux命令(1)：ls命令

ls命令是linux下最常用的命令。ls命令就是list的缩写，缺省下ls用来打印出当前目录的清单。如果ls指定其他目录，那么就会显示指定目录里的文件及文件夹清单。 通过ls 命令不仅可以查看linux文件夹包含的文件而且可以查看文件权限(包括目录、文件夹、文件权限)查看目录信息等等。ls 命令在日常的linux操作中用的很多!

> 1.命令格式

```shell
ls [选项]... [文件]...
```

> 2.命令功能

列出目标目录中所有的子目录和文件。

> 3.常用参数

```shell
# 必选参数对长短选项同时适用。
  -a, --all					# 不隐藏任何以. 开始的项目
  -A, --almost-all			# 列出除. 及.. 以外的任何项目
      --author				# 与-l 同时使用时列出每个文件的作者
  -b, --escape				# 以八进制溢出序列表示不可打印的字符
      --block-size=SIZE     # 在打印之前通过SIZE缩放尺寸;例如'block-size = M'以1,048,576字节为单位打印尺寸;请参阅下面的SIZE格式
  -B, --ignore-backups      # 不列出以~结尾的隐含条目
  -c                        # 与-lt：排序，和显示，ctime（文件状态信息的最后修改的时间）;与-l：显示ctime和按名称排序;否则：按ctime排序，最新的第一
  -C                        # 按列列出条目
      --color[=WHEN]        # 着色输出; WHEN可以是“always”（默认为省略），'auto'或'never'。 更多信息下面
  -d, --directory           # 列出目录本身，而不是它们的内容
  -D, --dired               # 生成为Emacs的direct模式设计的输出
  -f                        # 不排序，启用-aU，禁用-ls --color
  -F, --classify            # 将附加指示符（* / => @ |之一）附加到条目
      --file-type           # 同样，除了不附加“*”
      --format=WORD         # 跨-x，逗号-m，水平-x，长-l，单列-1，详细-l，垂直-C
      --full-time           # 像-l --time-style = full-iso
  -g						# 类似-l，但不列出所有者
      --group-directories-first
                            # 组文件之前的目录; 可以使用--sort选项进行扩充，但任何使用--sort = none（-U）都会禁用分组
  -G, --no-group            # 在长列表中，不打印组名称
  -h, --human-readable      # 与-l和/或-s，打印人类可读的大小（例如，1K 234M 2G）
      --si                  # 同样，但使用1000的权力，而不是1024
  -H, --dereference-command-line
                            # 请按照命令行中列出的符号链接
      --dereference-command-line-symlink-to-dir
                            # 按照每个命令行指向目录的符号链接
      --hide=PATTERN        # 不列出匹配shell PATTERN的隐含条目（被-a或-A覆盖）
      --indicator-style=WORD # 将带有样式WORD的指示符附加到条目名称：none（默认值），斜杠（-p），文件类型（ - 文件类型），分类（-F）
  -i, --inode               # 打印每个文件的索引号
  -I, --ignore=PATTERN      # 不列出匹配shell PATTERN的隐含条目
  -k, --kibibytes           # 默认为1024字节块用于磁盘使用
  -l						# 使用较长格式列出信息
  -L, --dereference			# 当显示符号链接的文件信息时，显示符号链接所指示的对象而并非符号链接本身的信息
  -m						# 所有项目以逗号分隔，并填满整行行宽
  -n, --numeric-uid-gid		# 类似 -l，但列出UID 及GID 号
  -N, --literal				# 输出未经处理的项目名称 (如不特别处理控制字符)
  -o						# 类似 -l，但不列出有关组的信息
  -p,  --indicator-style=slash	# 对目录加上表示符号"/"
  -q, --hide-control-chars  # 打印？ 而不是非文字字符
      --show-control-chars  # 显示非字母字符（默认，除非程序是'ls'和输出是一个终端）
  -Q, --quote-name          # 将条目名称括在双引号中
      --quoting-style=WORD  # 使用引用样式WORD用于条目名称：文字，语言环境，shell，shell-always，shell-escape，shell-escape-always，c，escape
  -r, --reverse				# 逆序排列
  -R, --recursive			# 递归显示子目录
  -s, --size				# 以块数形式显示每个文件分配的尺寸
  -S                        # 按文件大小排序，最大首先
      --sort=WORD           # 按WORD而不是名称排序：none（-U），size（-S），time（-t），version（-v），extension（-X）
      --time=WORD           # 与-l，显示时间为WORD而不是默认修改时间：atime或访问或使用（-u）; ctime或status（-c）; 也使用指定的时间作为排序键if --sort = time（最新的第一）
      --time-style=STYLE    # 与-l，显示时间使用样式STYLE：full-iso，long-iso，iso，语言环境或+ FORMAT; FORMAT解释像'date'; 如果FORMAT是FORMAT1 <newline> FORMAT2，则FORMAT1适用于非最近的文件，FORMAT2适用于最近的文件;如果STYLE的前缀为'posix-'，则STYLE仅在POSIX语言环境外生效
  -t                        # 按修改时间排序，最新的第一
  -T, --tabsize=COLS        # 假设选项卡停在每个COLS而不是8
  -u                        # 使用-lt：sort by和show，访问时间;使用-l：显示访问时间并按名称排序;否则：按访问时间排序，最新的
  -U                        # 不分类; 以目录顺序列出条目
  -v                        # 文本中的自然排序的（版本）数字
  -w, --width=COLS          # 将输出宽度设置为COLS。 0表示没有限制
  -x                        # 按行而不是按列列出条目
  -X                        # 按字母顺序按入口扩展排序
  -Z, --context             # 打印每个文件的任何安全上下文
  -1                        # 每行列出一个文件。 避免'\ n'与-q或-b
      --help				# 显示此帮助信息并退出
      --version				# 显示版本信息并退出

# SIZE参数是一个整数和可选单位（例如：10K是10 * 1024）。
# 单位是K，M，G，T，P，E，Z，Y（1024的幂）或KB，MB ...（1000的幂）。

# 使用色彩来区分文件类型的功能已被禁用，默认设置和 --color=never 同时禁用了它。
# 使用 --color=auto 选项，ls 只在标准输出被连至终端时才生成颜色代码。
# LS_COLORS 环境变量可改变此设置，可使用 dircolors 命令来设置。

# 退出状态：
# 0  正常
# 1  一般问题 (例如：无法访问子文件夹)
# 2  严重问题 (例如：无法使用命令行参数)
```

