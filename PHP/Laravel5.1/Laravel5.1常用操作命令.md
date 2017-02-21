## Laravel5.1常用操作命令

```shell
# 生成数据库迁移文件，该命令生成的迁移文件位于项目根目录下的database/migrations目录
php artisan make:migration create_tasks_table --create=tasks
Created Migration: 2017_01_17_090910_create_tasks_table
# 运行迁移
php artisan migrate
```

[Illuminate\Database\QueryException]                                         
  could not find driver (SQL: select * from information_schema.tables where t  
  able_schema = quickstart and table_name = migrations)    

```shell
sudo apt-get install php7.0-mysql
```

[Illuminate\Database\QueryException]                                         
  SQLSTATE[HY000][2002] No such file or directory (SQL: select * from inform  
  ation_schema.tables where table_schema = quickstart and table_name = migrat  
  ions)

```shell
# 数据库连接localhost修改成127.0.0.1
sudo vim .env
```

