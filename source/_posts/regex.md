---
title: "正则表达式快速上手"
tags: ["中文","正则"]
categories: ["regex","入门"]
cover: https://random.imagecdn.app/376/252
top_img: https://random.imagecdn.app/1920/400
date: 2020-04-06T20:56:29+08:00
---

## 基本规则  

* \d	匹配一个数字字符。等价于`[0-9]`  
\D	匹配一个非数字字符。等价于`[^0-9]`  

* \w	匹配包括下划线的任何单词数字字符。等价于 `[A-Za-z0-9_]`  
\W	匹配任何非单词数字字符。等价于 `[^A-Za-z0-9_]`  

* \f	 匹配一个换页符  
\n	匹配一个换行符   
\r	   匹配一个回车符  
\t	匹配一个制表符   
\v	匹配一个垂直制表符   
\s	匹配任何空白字符，包括空格、制表符、换页符等等。等价于 [ \f\n\r\t\v]  
\S	匹配任何非空白字符。等价于 `[^ \f\n\r\t\v]`  
`[\u4E00-\u9FA5]`  匹配中文字符  

*  \b     匹配单词边界(单词等于数字,字母),比如 `\b4\b` 匹配4,不匹配"34","45","345"," 4 "  
 \B     匹配非单词边界。`er\B` 能匹配 "verb" 中的 'er'，但不能匹配 "never" 中的 'er'。

* ^开始位置  
$结束位置  
*任意匹配次数(无所谓有没有出现)  
+匹配至少一次(至少要出现个一次)  
?匹配最多一次(出现个1次或者别出现)  

---

## 修饰符  
* `g`:全局匹配  
* `i`:忽略大小写  


---

## 特殊查找  

* `(?=pattern)`  正向预查,从pattern位置开始预查,匹配成功后继续从pattern位置开始匹配  
`(?:pattern)`   pattern匹配成功后跳过pattern匹配  
      比如:  `Windows(?:98|2000|XP)ABC`,匹配到98后开始匹配ABC,   `Windows(?=98|2000|XP)ABC`,匹配到98后匹配ABC  

* 肯定式向前查找  
   匹配字符序列Start后跟一个空格和Test字符序列(不区分大小写)  
   正则模式：`Start(?= Test)`  
   匹配字符序列some，如果在同一句子中还存在字符序列some  
   正则模式：`some(?=.*some.*)`  

* 否定式向前查找  
   匹配字符序列Start后面不存在test字符序列  
   正则模式：`Start (?!test)`  
   匹配Start 后面不存在test的行  
   正则模式: `^.*Start((?!test).)*$`  

* 肯定式向后查找  
   匹配前面有"rt"的字符序列Test  
   正则模式：`(?<=rt )Test`

* 否定式向后查找  
   匹配前面没有"rt "的字符序列Test  
   正则模式：`(?<!rt) Test`  

---

## 实际应用  
### 例子  

* `\d+\.\d+` 匹配小数  
* `[A-Z][a-z]*( [a-z]+)*\.$` 匹配简单英文句  
* `^(([0-1][0-9])|(2[0-3]))(:[0-5]\d){2}$` 匹配时分秒  

### vim  
* `:%s/foo/bar/g` 会在全局范围(%)查找foo并替换为bar，所有出现都会被替换（g）  

---

## JavaScript  
