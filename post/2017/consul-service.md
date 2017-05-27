```toml
title = "consul服务注册与服务发现"
slug = "consul-service"
desc = "consul服务注册与服务发现"
date = "2017-05-27 18:14:24"
update_date = "2017-05-27 18:14:24"
author = "tcc"
thumb = ""
draft = false
tags = ["consul"]
```

###consul介绍

[git地址](https://github.com/hashicorp/consul "git地址")

###使用goapi实现服务注册

> consul地址：10.10.222.19
服务地址：10.10.92.222
以下程序使用gin框架实现

```
    package main
    
    import (
            "github.com/gin-gonic/gin"
            "om-api/api"
            consulapi "github.com/hashicorp/consul/api"
            "fmt"
            "log"
    )
    
    const Id = "test"
    
    func main() {
            TestRegister()
            r := gin.Default()
            r.GET("/check", func(c *gin.Context) {
                    c.JSON(200, gin.H{
                            "code" : 200,
                    })
            })
    
            r.Run("0.0.0.0:5203") 
    }
    
    func TestRegister() {
            fmt.Println("test begin .")
            config := consulapi.DefaultConfig()
            config.Address = "10.10.222.19:8500"
    
            //config.Address = "localhost"
            fmt.Println("defautl config : ", config)
            client, err := consulapi.NewClient(config)
            if err != nil {
                    log.Fatal("consul client error : ", err)
            }
    
            //创建一个新服务。
            registration := new(consulapi.AgentServiceRegistration)
            registration.ID = Id
            registration.Name = "test"
            registration.Port = 5203
            registration.Tags = []string{"test"}
            registration.Address = "127.0.0.1"
            //增加check。
            check := new(consulapi.AgentServiceCheck)
            check.HTTP = fmt.Sprintf("http://%s:%d%s", registration.Address, registration.Port, "/check")
            check.Timeout = "5s"
            check.Interval = "5s"
            //注册check服务。
            registration.Check = check
            log.Println("get check.HTTP:", check)
    
            err = client.Agent().ServiceRegister(registration)
    
            if err != nil {
                    log.Fatal("register server error : ", err)
            }
    }
```

运行代码则会注册该服务到consul
###使用HTTP GET发现该服务
`http://10.10.222.19:8500/v1/health/service/test?passing=true`

返回值如下：
```
[
  {
    "Node": {
      "ID": "3ab01748-5a81-b1b8-04c0-340e34654028",
      "Node": "Lin-Dev",
      "Address": "127.0.0.1",
      "Datacenter": "dc1",
      "TaggedAddresses": {
        "lan": "127.0.0.1",
        "wan": "127.0.0.1"
      },
      "Meta": {},
      "CreateIndex": 5,
      "ModifyIndex": 6
    },
    "Service": {
      "ID": "test",
      "Service": "test",
      "Tags": [
        "test"
      ],
      "Address": "10.10.92.222",
      "Port": 5203,
      "EnableTagOverride": false,
      "CreateIndex": 11,
      "ModifyIndex": 11
    },
    "Checks": [
      {
        "Node": "Lin-Dev",
        "CheckID": "serfHealth",
        "Name": "Serf Health Status",
        "Status": "passing",
        "Notes": "",
        "Output": "Agent alive and reachable",
        "ServiceID": "",
        "ServiceName": "",
        "ServiceTags": [],
        "CreateIndex": 5,
        "ModifyIndex": 5
      },
      {
        "Node": "Lin-Dev",
        "CheckID": "service:test",
        "Name": "Service 'test' check",
        "Status": "passing",
        "Notes": "",
        "Output": "HTTP GET http://10.10.92.222:5203/check: 200 OK Output: {\"code\":200}\n",
        "ServiceID": "test",
        "ServiceName": "test",
        "ServiceTags": [
          "test"
        ],
        "CreateIndex": 11,
        "ModifyIndex": 315
      }
    ]
  }
]
```
