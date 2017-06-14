```toml
title = "使用tideways和xhgui搭建PHP性能分析平台"
slug = "php-performance-analysis"
desc = "使用tideways和xhgui搭建PHP性能分析平台"
date = "2017-06-14 20:30:24"
update_date = "2017-06-14 20:30:24"
author = "tcc"
thumb = ""
draft = false
tags = ["tideways","xhgui","php"]
```

##背景
> 一直想做个性能分析工具，在代码中埋点不但麻烦，还污染现有代码。一开始看到了xhprof，官方版本已经不维护了。后来看到了tideways可以做无侵入监控，变了解了下，[官网地址](https://tideways.io "官网地址")。

##安装
参考官网：[安装方法](https://tideways.io/profiler/docs/setup/installation#redhatfedoracentos "安装方法")

安装后再`/usr/lib/tideways`文件夹下会生成各个版本的`.so`文件，找到你所使用的版本的扩展文件，拷贝到扩展文件夹，并将其加入到`php.ini`中。重启`php-fpm`，安装成功。

##安装xhgui
英文版地址：[perftools/xhgui](https://github.com/perftools/xhgui "perftools/xhgui")
中文版地址：[laynefyc/xhgui-branch](https://github.com/laynefyc/xhgui-branch "laynefyc/xhgui-branch")
>注意，xhgui依赖mongodb扩展，务必确保已经安装。安装完毕后修改xhgui/config/config.default.php相应的配置项。

mongodb使用的db默认为`xhprof`，可在xhgui中自行配置。
为mongodb加索引：
     > db.results.ensureIndex( { 'meta.SERVER.REQUEST_TIME' : -1 } )
     > db.results.ensureIndex( { 'profile.main().wt' : -1 } )
     > db.results.ensureIndex( { 'profile.main().mu' : -1 } )
     > db.results.ensureIndex( { 'profile.main().cpu' : -1 } )
     > db.results.ensureIndex( { 'meta.url' : 1 } )

##xhgui nginx配置
    server {
            charset utf-8;
            listen       80;
            server_name  xhgui.tccbest.com;
            root /xxx/xxx/xhgui/webroot;
            index  index.html index.htm index.php;

            location / {
                    try_files $uri $uri/ /index.php?$args;
            }

            location ~ \.php$ {
                root           /xxx/xxx/xhgui/webroot;
                fastcgi_pass   127.0.0.1:9000;
                fastcgi_index  index.php;
                fastcgi_param  SCRIPT_FILENAME $document_root$fastcgi_script_name;
                include        fastcgi_params;
                try_files      $uri = 404;
            }
    }

访问`xhgui.tccbest.com`展示如下页面：

[![xhgui](https://dn-myfms.qbox.me/xhgui.png "xhgui")](https://dn-myfms.qbox.me/xhgui.png "xhgui")

##应用nginx配置
将以下两行加入到项目的nginx配置中

    fastcgi_param TIDEWAYS_SAMPLERATE "25";
    fastcgi_param PHP_VALUE "auto_prepend_file={xhgui-path}/xhgui/external/header.php";

重启nginx生效


