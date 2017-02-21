

## linux压缩和解压缩命令大全

##### tar命令

```shell
tar zxvf FileName.tar # 解包
tar czvf FileName.tar DirName # 打包
```

##### gz命令

```shell
gunzip FileName.gz # 解压
gzip -d FileName.gz # 解压
gzip FileName.tar.gz # 压缩
gzip FileName.tgz # 压缩
tar -zxvf FileName.tar.gz # 解压
tar -zcvf FileName.tar.gz DirName # 压缩
tar -zcvf FileName.tar.gz DirName1 DirName2 DirName3 ... # 压缩多个文件
```

##### bz2命令

```shell
bzip2 -d FileName.bz2 # 解压
bunzip2 FileName.bz2 # 解压
bzip2 -z FileName.tar.bz2 # 压缩
tar -jxvf FileName.tar.bz2 # 解压
tar -jcvf FileName.tar.bz2 DirName # 压缩
```

##### bz命令

```shell
bzip2 -d FileName.bz # 解压
bunzip2 FileName.bz # 解压
tar -jxvf FileName.tar.bz # 解压
```

##### Z命令

```shell
uncompress FileName.Z # 解压
compress FileName.tar.Z # 压缩
tar -zxvf FileName.tar.Z # 解压
tar -zcvf FileName.tar.Z DirName # 压缩
```

##### zip命令

```shell
unzip FileName.zip # 解压
zip FileName.zip DirName # 压缩
```
##### xz命令

```shell
xz -d FileName.tar.xz # 解压成tar文件
tar zxvf FileName.tar # 解包
```