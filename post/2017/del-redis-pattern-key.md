```toml
title = "Redis删除匹配的key"
slug = "del-redis-pattern-key"
desc = "Redis删除匹配的key"
date = "2017-03-01 17:14:16"
update_date = "2017-03-22 22:04:16"
author = "tcc"
thumb = ""
draft = false
tags = ["Redis"]
```

    redis-cli [-a <password>][-h <host>][-n <db>] KEYS "pattern" | xargs redis-cli [-a <password>][-h <host>][-n <db>] DEL
其中pattern是keys命令支持的模式


