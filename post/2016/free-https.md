```toml
title = "如何搭建免费的HTTPS服务"
slug = "如何搭建免费的HTTPS服务"
desc = "如何搭建免费的HTTPS服务"
date = "2016-11-25 15:28:16"
update_date = "2017-03-22 22:04:16"
author = "tcc"
thumb = ""
draft = false
tags = ["https"]
```

最近看到谷歌放大招：2017年起将把HTTP网站标记为不安全
并且谷歌和百度均宣布优先收录HTTPS网站，所以闲着把自己的站点升级成了HTTPS

## HTTPS服务提供商
我使用的是startssl, 可以免费使用三年的HTTPS服务。

去网站注册登录，并完成域名和邮箱验证，完成后看下面

![](https://dn-myfms.qbox.me/1.png)
![](https://dn-myfms.qbox.me/2.png)

依次点击图片中的链接

然后在自己机器的nginx目录下执行
```
openssl req -newkey rsa:2048 -keyout yourname.key -out yourname.csr
```

会生成两个文件, 复制 .csr 文件中的内容到下图红色处

![](https://dn-myfms.qbox.me/3.png)

提交后进入到 **Tool Box** 下的 **Certificate** List，看到域名了就代表设置成功

下载设置好的证书，把证书放到服务器nginx配置目录的ssl文件夹中

## 配置Nginx

新建 **tccbest.conf** ，把所有的 http 请求 301 到 https 中
```
server {
  listen       	  80;
  server_name     a.tccbest.com;
  return       	  301 https://$server_name$request_uri;
}
```


新建 **tccbest_ssl.conf**
```
server {
        listen       443 ssl;
        server_name  a.tccbest.com;
       	ssl on;
       	ssl_certificate ssl/a.tccbest.com_bundle.crt;
       	ssl_certificate_key ssl/tccbest.key;
    }
```

到此配置结束，访问网站，变成了HTTPS，并且带上了小绿标

![](https://dn-myfms.qbox.me/4.png)






