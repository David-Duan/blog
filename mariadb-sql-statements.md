---
title: "Mariadb Sql Statements"
date: 2018-02-07T12:32:30+11:00
draft: false
tags: ["database", "mariadb"]
categories: ["DBA"]
---
```shell
mysql
mysql db_name
mysql --user=user_name --password db_name
mysql db_name < script.sql > output.tab
```
# User
```sql
SELECT host, user FROM mysql.user;
CREATE OR REPLACE USER 'foo2'@'%' IDENTIFIED BY 'password';
CREATE USER IF NOT EXISTS 'foo2'@'192.168.0.3' IDENTIFIED BY 'password';
DROP USER IF EXISTS name;
```

# Privileges
```sql
GRANT SELECT ON db_name.table1 to 'joffrey'@'192.168.0.3';
GRANT SELECT ON db_name.table2 to 'joffrey'@'%';
GRANT ALL PRIVILEGES ON  db_name.* to 'alexander'@'localhost' WITH GRANT OPTION;
```

# Database
```sql
show databases;
CREATE DATABASE db1;
```


# Table
```sql
show tables;
```

