```toml
title = "MongoDB处理sort排序报超出内存最大值错误"
slug = "mongodb-sort-max-ram"
desc = "MongoDB处理sort排序报超出内存最大值错误"
date = "2017-03-20 11:59:28"
update_date = "2017-03-22 21:59:28"
author = "tcc"
thumb = ""
draft = false
tags = ["MongoDB"]
```
mongodb中find时使用sort报错

> Executor error during find command: OperationFailed: Sort operation used more than the maximum 33554432 bytes of RAM. Add an index, or specify a smaller limit.

 解决方案： 

     db.adminCommand({setParameter: 1, internalQueryExecMaxBlockingSortBytes:50151432})

或者使用aggregate，并将allowDiskUse置为true（默认为false，RAM限制为100M）
