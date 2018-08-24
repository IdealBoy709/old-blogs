---
title: HTML学些资料整理
categories: web
tags: HTML
---
+ utf-8和utf8的区别？

"UTF-8" 是标准写法，php 在 Windows 下边英文不区分大小写，所以也可以写成 "utf-8"。"UTF-8" 也可以把中间的"-"省略，写成 "UTF8"。一般程序都能识别，但也有例外（如下文），为了严格一点，最好用标准的大写"UTF-8"。
在数据库中只能使用"utf8"(MySQL)，在MySQL的命令模式中只能使用“utf8”，不能使用“utf-8”，也就是说在PHP程序中只能使用“set names utf8(不加小横杠)”，如果你加了'-'此行命令将不会生效，但是在PHP中Header时却要加上“-”，因此IE不认识没有


