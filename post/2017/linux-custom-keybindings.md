```toml
title = "使用Linux命令行中的快捷键"
slug = "linux-custom-keybindings"
desc = "使用Linux命令行中的快捷键"
date = "2017-05-26 18:47:19"
update_date = "2017-05-26 18:47:19"
author = "tcc"
thumb = ""
draft = false
tags = ["linux"]
```
 
本文转自[Gong Yong的Blog](http://gywbd.github.io/posts/2014/11/linux-keybindings.html "Gong Yong的Blog")
快捷键(Keybinding)指将一个按键组合指定到某个动作。

我们通常很熟悉的两个快捷键是：

- Control-c ：复制
- Control-v ：粘贴

这篇文章会介绍命令行环境提供的一些默认的快捷键（也会告诉你在哪里找到这些命令，特别是当你忘记了的时候）。

Linux命令行中有很默认的快捷键，它们使得编辑命令更方便。它们由一个名为Readine的工具提供。

这里有一些是我经常用到的（如果你熟悉Emacs，对这些快捷键你会有些似曾相识的感觉）。

###移动快捷键
下面这些快捷键用于移动：

- Control-a	将光标移到行首
- Control-e	将光标移到当前行最后一个字符的后面
- Control-f	将光标前移一个字符（跟方向键一样）
- Control-b	将光标后移一个字符（跟方向键一样）

###删除快捷键
下面这些快捷键用于删除操作：

- Control-k	删除光标后面的所有字符（包括光标）
- Control-u	删除光标前面的所有字符（不包括光标）
- Control-w	删除光标前面的单词（单词指由非空格符组成的字符序列）
- Control-h	删除光标前面的字符（跟backspace一样）
- Control-d	删除当前光标下面的字符（跟delete一样，如果当前光标下没有字符则退出）

###历史快捷键
下面这些快捷键用于操作命令行历史记录：

- Control-p	切换到上一个命令
- Control-n	切换到下一个命令
- Control-r	反向索引查询（通过输入命令的一部分从命令历史中查询匹配的命令，根据命令使用时的时间逆序查询，也就是会先匹配最近使用的命令）

###其他快捷键
下面的是一些其他的比较有用的快捷键

- Control-l	清除屏幕（类似clear命令）
- Control-j	执行当前命令（类似回车键）
- Control-c	终止当前命令，返回命令提示符
- Control-？	撤销最后一次编辑
- Control-/	重做最后一次撤销的编辑

bind命令可以查看所有的快捷键（如果你忘记了某个快捷键的话，可以使用这个命令找到）

    $ bind -p

这个命令的输出是这个样子

    "\C-g": abort
    "\C-x\C-g": abort
    "\e\C-g": abort
    "\C-j": accept-line
    …
这个输出的格式是：

`组合键 ： 绑定 `

注意你必须使用这个格式来自定义快捷键。

记住你可以使用grep查找你感兴趣的绑定。

例如下面这个命令查找所有使用了Control键的绑定：

    $ bind -p | grep '\\c' 

注意这里的有两个转义符，第一个转义符用于转义第二个反斜线。