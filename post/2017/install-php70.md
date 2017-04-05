```toml
title = "编译安装PHP7"
slug = "install-php70"
desc = "编译安装PHP7"
date = "2017-04-05 14:41:57"
update_date = "2017-04-05 14:41:57"
author = "tcc"
thumb = ""
draft = false
tags = ["PHP"]
```
1. 下载PHP源码包，并解压，进入到源码包目录，以`/root/php-7.0.17`为例
2. 执行命令
`./configure --prefix=/usr/local/php70 \
--enable-fpm \
--with-fpm-user=www \
--with-fpm-group=www \
--with-config-file-path=/usr/local/php70/etc \
--with-config-file-scan-dir=/usr/local/php70/etc/php.d \
--with-pcre-regex \
--with-zlib \
--with-openssl \
--enable-bcmath \
--with-curl \
--with-gd \
--with-freetype-dir=/usr/local/php70 \
--with-jpeg-dir=/usr/local/php70 \
--with-png-dir=/usr/local/php70 \
--enable-gd-native-ttf \
--with-gmp \
--with-mhash \
--enable-mbstring \
--with-mcrypt \
--with-pdo-mysql \
--with-readline \
--with-openssl-dir \
--with-xmlrpc \
--with-xsl \
--enable-zip \
--enable-mysqlnd \
--with-pear`
3. 在第2步中，通常会缺少扩展，执行`yum install libcurl-devel libxml2-devel gmp-devel libmcrypt-devel readline-devel libxslt-devel libjpeg-devel libpng-devel freetype-devel`
4. make && make install 
5. 依次执行以下命令
`groupadd www
  useradd -g www www
  cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm
  chmod +x /etc/init.d/php-fpm
  cp php.ini-development /usr/local/php70/etc/php.ini
  cp /usr/local/php70/etc/php-fpm.conf.default /usr/local/php70/etc/php-fpm.conf
  cp /usr/local/php70/etc/php-fpm.d/www.conf.default /usr/local/php70/etc/php-fpm.d/www.conf
  ln -sf /usr/local/php70/bin/php /usr/local/bin/php
  ln -sf /usr/local/php70/bin/php /usr/bin/php
  service php-fpm start`
  到此，php安装完毕<br>
6. 使用`pecl`安装扩展:`/usr/local/php70/bin/pecl install mongodb`，在`/usr/local/php70/etc/php.ini`中加入`extension=mongodb.so`
