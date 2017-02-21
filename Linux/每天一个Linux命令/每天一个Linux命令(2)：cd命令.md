## 每天一个Linux命令(2)：cd命令

Linux cd 命令可以说是Linux中最基本的命令语句，其他的命令语句要进行操作，都是建立在使用 cd 命令上的。

> 1.命令格式

```shell
cd [目录名]
```

> 2.命令功能

切换到当前目录至dirName

> 3.常用范例

1. 跳转到指定目录：cd dir

   dir 可以是绝对路径也可以是相对路径。

   dir / 即是跳转到根目录。

   dir 还可是通配符，如：cd a* cd a*b cd a*/p*等。

2. 跳转到主目录：cd 或 cd ~

3. 跳转到上一级：cd ..

4. 跳转到上次所在目录：cd -

   如：cd /home/test/test1 此时在/home/test/test1下

   cd 此时在root下

   cd - 此时又回到了/home/test/test1下

5. 跳转到上一命令所指位置：cd !$

   将上一个命令的参数作为cd的目录