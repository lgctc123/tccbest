```toml
title = "使用filebeat搜集日志到es问题汇总"
slug = "es-filebeat"
desc = ""
date = "2018-04-03 14:35:40"
update_date = "2017-04-03 14:35:40"
author = "tcc"
thumb = ""
draft = false
tags = ["filebeat","elasticsearch"]
```
启动es报错信息
```
[2] bootstrap checks failed
[1]: max number of threads [1024] for user [elasticsearch] is too low, increase to at least [4096]
[2]: system call filters failed to install; check the logs and fix your configuration or disable system call filters at your own risk
```

[1]解决：切换到root用户，进入limits.d目录下修改配置文件。
```
vim /etc/security/limits.d/90-nproc.conf
修改如下内容：
* soft nproc 1024
修改为
* soft nproc 4096
```

[2]解决：在elasticsearch.yml中，注意要在Memory下面:
```
bootstrap.memory_lock: false
bootstrap.system_call_filter: false
```
