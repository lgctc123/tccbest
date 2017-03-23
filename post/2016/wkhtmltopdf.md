```toml
title = "使用wkhtmltopdf遇到的问题总结"
slug = "使用wkhtmltopdf遇到的问题总结"
desc = "使用wkhtmltopdf遇到的问题总结"
date = "2016-12-01 10:26:16"
update_date = "2017-03-22 22:04:16"
author = "tcc"
thumb = ""
draft = false
tags = ["wkhtmltopdf"]
```
最近产品提了个需求，需要把内容导出成pdf，于是在github上搜索了一把  
最终试用了`dompdf/dompdf`和`KnpLabs/snappy`

结合自身业务需求，最终选用了`KnpLabs/snappy`

###遇到的问题
今天遇到代码报错
`Exit with code 1 due to network error: ContentNotFoundError`

经过谷歌的帮助，查到了以下信息 

| Exit Code | Explanation | 
| ------| ------ | ------ |
| 0	| All OK |
| 1 | PDF generated OK, but some request(s) did not return HTTP 200 |
| 2 | Could not something something |
| X | Could not write PDF: File in use |
| Y | Could not write PDF: No write permission |
| Z | PDF generated OK, but some JavaScript requests(s) timeouted |
| A | Invalid arguments provided |
| B | Could not find input file(s) |
| C | Process timeout |

所以对应的`code 1`应该是生成pdf的html中存在对外的请求，并且返回的状态码不是200  

把生成pdf的html写成一个html文件，最终发现有张图片请求返回的是状态码400，因此换了个图片，生成pdf成功！！

