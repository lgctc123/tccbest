```toml
title = "Git修改远程仓库地址"
slug = "change-git-remote-url"
desc = "Git修改远程仓库地址"
date = "2018-01-07 22:26:16"
update_date = "2017-03-24 19:01:57"
author = "tcc"
thumb = ""
draft = false
tags = ["Git"]
```
1.直接修改
```
git remote set-url origin [url]

```

2.先删后改
```
git remote rm origin
git remote add origin [url]

```
