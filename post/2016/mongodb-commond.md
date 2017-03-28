```toml
title = "MongoDB常用命令"
slug = "mongodb-commond"
desc = "mongodb常用命令"
date = "2016-12-07 11:27:16"
update_date = "2017-03-22 22:04:16"
author = "tcc"
thumb = ""
draft = false
tags = ["MongoDB"]
```
1. 新建用户
`db.createUser({"user":"user","pwd":"pwd","roles":[{"db":"db","role":"readWrite"}]});`


