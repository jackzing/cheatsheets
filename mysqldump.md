---
title: mysqldump
updated: 2020-07-16
layout: 2017/sheet
category: Databases
intro: |
   mysqldump是备份MySQL数据库的有效工具。它使用DROP表，CREATE表和INSERT到源数据库的sql语句中创建一个* .sql文件。要还原数据库，请在目标数据库上执行* .sql文件。使用mysqldump，可以使用单个命令备份本地数据库并同时将其还原到远程数据库上。
---

### 备份单个数据库

```shell
# mysqldump -u root -ptmppassword testdb > testdb.sql
# mysqldump -u root -p[root_password] [database_name] > dumpfilename.sql
```

### 备份多个数据库

```shell
# mysqldump -u root -ptmppassword --databases testdb testdb1 > testdb.sql
```

### 备份所有数据库

```
# mysqldump -u root -ptmppassword --all-databases > /tmp/all-database.sql
```

### 备份数据库中一张表

```
# mysqldump -u root -ptmppassword testdb tb_student > /tmp/testdb-tb_student.sql
```

###  恢复单个数据库

```
# mysql -u root -p[root_password] [database_name] < dumpfilename.sql
# mysql -u root -ptmppassword testdb < /tmp/testdb.sql
```

### 备份本地数据库，从远程数据库恢复

```shell
# mysqldump -u root -ptmppassword testdb | mysql \
    -u root -ptmppassword --host=remote-server -C testdb
```
