## mysqldump常用于MySQL数据库逻辑备份

各种用法说明

最简单的用法

```shell
mysqldump -uroot -ppassword [database name] > [dump file]
# 上述命令将指定数据库备份到某dump文件（转储文件）中，比如：
mysqldump -uroot -proot test > test.dump
# 生成的test.dump文件中包含建表语句（生成数据库结构哦）和插入数据的insert语句
```

--opt

     如果加上--opt参数则生成的dump文件中稍有不同：

- 建表语句包含drop table if exists tableName
- insert之前包含一个锁表语句lock tables tableName write，insert之后包含unlock tables

跨主机备份

     使用下面的命令可以将host1上的sourceDb复制到host2的targetDb，前提是host2主机上已经创建targetDb数据库：

```shell
mysqldump --host=host1 --opt sourceDb| mysql --host=host2 -C targetDb
```

-C指示主机间的数据传输使用数据压缩

     D. 只备份表结构

```shell
mysqldump --no-data --databases mydatabase1 mydatabase2 mydatabase3 > test.dump
```

     将只备份表结构。--databases指示主机上要备份的数据库。如果要备份某个MySQL主机上的所有数据库可以使用--all-databases选项，如下：

```shell
mysqldump --all-databases > test.dump
```

     E. 从备份文件恢复数据库

```shell
mysql [database name] < [backup file name]
```

**2、**结合Linux的cron命令实现定时备份

比如需要在每天凌晨1:30备份某个主机上的所有数据库并压缩dump文件为gz格式，那么可在/etc/crontab配置文件中加入下面代码行：

```shell
30 1 * * * root mysqldump -u root -pPASSWORD --all-databases | gzip > /mnt/disk2/database_`date '+%m-%d-%Y'`.sql.gz
```

前面5个参数分别表示分钟、小时、日、月、年，星号表示任意。date '+%m-%d-%Y'得到当前日期的MM-DD-YYYY格式。

**3、**一个完整的Shell脚本备份MySQL数据库示例

```shell
#vi /backup/backup.sh

#!bin/bash
cd /backup
echo "You are in backup dir"
mv backup* /oldbackup
echo "Old dbs are moved to oldbackup folder"
File = backup-$Now.sql
mysqldump -u user -p password database-name > $File
echo "Your database backup successfully completed"
```

     上面脚本文件保存为backup.sh，并且系统中已经创建两个目录/olcbackup和/backup。每次执行backup.sh时都会先将/backup目录下所有名称为backup开头的文件移到/oldbackup目录。

      为上述脚本制定执行计划如下：

```shell
#crontab -e
30 1 * * * /backup.sh
```

 4、mysqldump全量备份+mysqlbinlog二进制日志增量备份

    从mysqldump备份文件恢复数据会丢失掉从备份点开始的更新数据，所以还需要结合mysqlbinlog二进制日志增量备份。确保my.ini或者my.cnf中包含下面的配置以启用二进制日志，或者mysqld ---log-bin：

```shell
[mysqld]
log-bin=mysql-bin
```

    mysqldump命令必须带上--flush-logs选项以生成新的二进制日志文件：

```shell
mysqldump --single-transaction --flush-logs --master-data=2 > backup.sql
```

    这样生成的增量二进制日志文件比如为mysql-bin.000003，那么恢复数据时如下：

   此外mysqlbinlog还可以指定--start-date、--stop-date、--start-position和--stop-position参数，用于精确恢复数据到某个时刻之前或者跳过中间某个出问题时间段恢复数据，直接摘录MySQL文档说明中相关内容如下：

```shell
5.9.3.1. 指定恢复时间
对于MySQL 4.1.4，可以在mysqlbinlog语句中通过--start-date和--stop-date选项指定DATETIME格式的起止时间。举例说明，假设在今天上午10:00(今天是2005年4月20日)，执行SQL语句来删除一个大表。要想恢复表和数据，你可以恢复前晚上的备份，并输入：
mysqlbinlog --stop-date="2005-04-20 9:59:59" /var/log/mysql/bin.123456 \
     | mysql -u root -pmypwd
该命令将恢复截止到在--stop-date选项中以DATETIME格式给出的日期和时间的所有数据。如果你没有检测到几个小时后输入的错误的SQL语句，可能你想要恢复后面发生的活动。根据这些，你可以用起使日期和时间再次运行mysqlbinlog：

mysqlbinlog --start-date="2005-04-20 10:01:00" /var/log/mysql/bin.123456 \
     | mysql -u root -pmypwd \
在该行中，从上午10:01登录的SQL语句将运行。组合执行前夜的转储文件和mysqlbinlog的两行可以将所有数据恢复到上午10:00前一秒钟。你应检查日志以确保时间确切。下一节介绍如何实现。

5.9.3.2. 指定恢复位置
也可以不指定日期和时间，而使用mysqlbinlog的选项--start-position和--stop-position来指定日志位置。它们的作用与起止日选项相同，不同的是给出了从日志起的位置号。使用日志位置是更准确的恢复方法，特别是当由于破坏性SQL语句同时发生许多事务的时候。要想确定位置号，可以运行mysqlbinlog寻找执行了不期望的事务的时间范围，但应将结果重新指向文本文件以便进行检查。操作方法为：
mysqlbinlog --start-date="2005-04-20 9:55:00" --stop-date="2005-04-20 10:05:00" \
      /var/log/mysql/bin.123456 > /tmp/mysql_restore.sql
该命令将在/tmp目录创建小的文本文件，将显示执行了错误的SQL语句时的SQL语句。你可以用文本编辑器打开该文件，寻找你不要想重复的语句。如果二进制日志中的位置号用于停止和继续恢复操作，应进行注释。用log_pos加一个数字来标记位置。使用位置号恢复了以前的备份文件后，你应从命令行输入下面内容：

mysqlbinlog --stop-position="368312" /var/log/mysql/bin.123456 \
    | mysql -u root -pmypwd 
 
mysqlbinlog --start-position="368315" /var/log/mysql/bin.123456 \
    | mysql -u root -pmypwd \ 
上面的第1行将恢复到停止位置为止的所有事务。下一行将恢复从给定的起始位置直到二进制日志结束的所有事务。因为mysqlbinlog的输出包括每个SQL语句记录之前的SET TIMESTAMP语句，恢复的数据和相关MySQL日志将反应事务执行的原时间。
```