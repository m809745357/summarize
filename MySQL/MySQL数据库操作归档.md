## MySQL数据库操作归档

> 创建按数据库用户，单独给数据库用户权限

```mysql
# 创建表
CREATE DATABASE `huishuo_appraisal` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
# 创建用户名appraisal密码huishuoit并授权ip为223.93.134.173
CREATE USER 'appraisal'@'223.93.134.173' IDENTIFIED BY 'huishuoit';
# 给予appraisal用户huishuo_appraisal数据库权限
GRANT ALL PRIVILEGES ON huishuo_appraisal.* TO 'appraisal'@'223.93.134.173' IDENTIFIED BY 'huishuoit';
# 刷新数据库权限表
FLUSH PRIVILEGES;
# 查看MYSQL数据库中所有用户
SELECT DISTINCT CONCAT('User: ''',user,'''@''',host,''';') AS `query` FROM mysql.user;
# 查看数据库中具体某个用户的权限
SHOW GRANTS FOR 'cactiuser'@'%';
SELECT * FROM mysql.user WHERE `user` = 'cactiuser' \G
# 删除某张表的某个字段
ALTER TABLE `agent`.`agent_users` 
DROP COLUMN `recommend_str`,
DROP COLUMN `recommend_id`;
```

