```toml
title = "RabbitMQ开启trace log"
slug = "rabbitmq-trace-log.md"
desc = "RabbitMQ开启trace log"
date = "2017-02-27 09:45:16"
update_date = "2017-03-22 22:04:16"
author = "tcc"
thumb = ""
draft = false
tags = ["RabbitMQ"]
```

###### 1.rabbitmq-plugins enable rabbitmq_tracing
###### 2.vim /etc/rabbitmq/rabbitmq.config 添加以下内容：
`[{rabbitmq_tracing, [{directory, "/var/log/rabbitmq"}, {username,  "username"},{password, "password"}]}].`
###### 3.打开控制台，`Admin->Tracing->Add a new trace`

