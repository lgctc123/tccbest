```toml
title = "MySQL常用"
slug = "mysql-command"
desc = "MySQL常用"
date = "2017-05-18 09:34:34"
update_date = "2017-03-24 09:34:34"
author = "tcc"
thumb = ""
draft = false
tags = ["MySQL"]
```
```
mysqldump -uusername -ppassword -h ip database table > file   导出数据库表
mysql  -uusername -ppassword -h ip < file 导入数据
grant all privileges on *.* to 'user'@'host' identified by 'pass' with grant option 给用户有所有权限（包含授权权限）
```
