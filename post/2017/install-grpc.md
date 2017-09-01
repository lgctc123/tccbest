```toml
title = "不翻墙安装grpc"
slug = "install-grpc"
desc = "安装grpc"
date = "2017-09-01 15:53:36"
update_date = "2017-09-01 15:53:36"
author = "tcc"
thumb = ""
draft = false
tags = ["grpc"]
```
```
1.mkdir -p $GOPATH/src/google.golang.org
2.cd $GOPATH/src/google.golang.org
3.git clone https://github.com/grpc/grpc-go.git grpc
4.git clone https://github.com/google/go-genproto.git genproto
5.mkdir -p $GOPATH/src/golang.org/x
6.cd $GOPATH/src/golang.org/x
7.git clone https://github.com/golang/net.git
8.git clone https://github.com/golang/text.git
```
