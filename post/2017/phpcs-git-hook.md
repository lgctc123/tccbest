```toml
title = "PHP规范代码 - git hook 配置PHPCS"
slug = "phpcs-git-hook"
desc = "PHP规范代码 - git hook 配置PHPCS"
date = "2017-06-13 18:14:05"
update_date = "2017-06-13 18:14:05"
author = "tcc"
thumb = ""
draft = false
tags = ["git","phpcs","hooks"]
```

##PHPCS
###安装
#####使用 composer:

    composer global require "squizlabs/php_codesniffer=*"

> 其他安装方式请自行查找。注意，你可能需要将 `~/.composer/vendor/bin/` 添加到 PATH 环境变量中，或者将` ~/.composer/vendor/bin/`中的`phpcs`和`phpcbf`软链到`/usr/local/bin/`否则会报命令找不到。

###使用
#####使用PSR2标准检测代码

`phpcs xxx.php --standard=PSR2` 

#####修复不符合PSR2标准的代码

`phpcbf xxx.php --standard=PSR2`

###git hook中检测

复制[pre-commit](https://github.com/lgctc123/git-hooks/blob/master/phpcs-pre-commit/pre-commit "pre-commit")中的内容到项目中的`{project_root}/.git/hooks/pre-commit`下，`chmod +x {project_root}/.git/hooks/pre-commit`。在提交代码时，不符合PSR2标准的文件将会报错。