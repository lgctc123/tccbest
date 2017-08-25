```toml
title = "记一次日志存储优化(mongodb)"
slug = "mongo-backup"
desc = "mongodb"
date = "2017-08-25 20:20:26"
update_date = "2017-08-25 20:20:26"
author = "tcc"
thumb = ""
draft = false
tags = ["mongodb"]
```

##### 背景
之前写的代码所有的日志都通过mongodb来存储和检索，目前硬盘200G已经使用了195G，监控一直报警。一开始通过精简已有日志中的字段，发现空间下降不明显。于是翻了下官方手册，刚好翻到mongodb的备份，想了想历史日志也用不着及时搜索，于是就备份了

##### 备份命令
    mongodump --archive=xxxx.archive --db db --collection collection

##### 压缩备份
    gzip xxxx.archive

##### 写个脚本删除备份的日志

##### 后续
##### 备份恢复命令
    mongorestore --gzip --archive=xxxx.archive.gz --db db

##### shell脚本
由于我的日志是按照日期分天存储，因此比较好导出，脚本如下

    #!/bin/bash
    a="mongodump --archive="
    b=".archive"
    c="--db php_log --collection "
    for i in $( seq $1 $2 )
    do
        collection="$3_$i"
        archive="$collection$b"
        $a$archive $c$collection
        gzip $archive
    done

脚本比较烂，不要嘲笑😂
