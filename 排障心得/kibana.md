# 常用命令集合

> elk作为常用的日志查询系统，使用高效的擦汗寻方法能帮助我们快速定位日志以及解决问题

## 1. 常用查询
- 1、要搜索一个确切的字符串，即精确搜索，需要使用双引号引起来：path:”/app/logs/nginx/access.log”

- 2、如果不带引号，将会匹配每个单词：uid token

- 3、模糊搜索：path:”/app/~

- 4、* 匹配0到多个字符：*oken

- 5、? 匹配单个字符 : tok?n

- 6、+：搜索结果中必须包含此项 -：不能含有此项 什么都没有则可有可无： +token -appVersion appCode

- 7、运算符AND/OR/NOT必须大写：token AND uid ；token OR uid；NOT uid

- 8、允许一个字段值在某个区间（[] 包含该值，{}不包含）：@version:[1 TO 3]

- 9、组合查询：(uid OR token) AND version

- 10、转义特殊字符 + – && || ! ( ) { } [ ] ^ ” ~ * ? : \ 转义特殊字符只需在字符前加上符号\

- 11、分组(firstname:H* OR age:20) AND state:KS 先查询名字H开头年龄或者是20的结果，然后再与国家是KS的结合

- 12、firstname:(+H* -He*) 搜索firstname字段里H开头的结果，并且排除firstname里He开头的结果

- 13.查询一，xxx:[1 TO *]
