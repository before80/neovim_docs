+++
title = "生成文档前的替换"
date = 2023-06-05T09:37:31+08:00
description = ""
isCJKLanguage = true
draft = false

+++

# 生成文档前的替换

```
{{< ref "">}}

// 在浏览器控制台中执行以下代码
var elements = document.querySelectorAll('p > font > font > font');

elements.forEach(function(element) {        
        var newline = document.createElement('br');
        element.parentNode.insertBefore(newline, element);        
        element.firstChild.nodeValue = '&zeroWidthSpace;' +element.firstChild.nodeValue;
});


```





## 替换使用`|xxx|`的高亮部分

```
// 查找匹配如下字符
\|([a-zA-Z\-\.\(\)]+)\|

// 替换成
`$1`
```

## 替换使用`>lua  <`的代码块

````
// 查找匹配如下正则表达式
>lua(\n)([^<]+)\n<

// 替换成 (注意前后多加一个新行)
$1$1
``` lua$1
$2
$1
```
$1$1

// 再次替换 以下字符(有空格开头)
 ```

// 替换成(无空格开头)
```
````

## 替换使用`>vim  <`的代码块

````
// 查找匹配如下正则表达式
>vim(\n)([^<]+)\n<

// 替换成 (注意前后多加一个新行)
$1$1
``` lua$1
$2
$1
```
$1$1

// 再次替换 以下字符(有空格开头)
 ```

// 替换成(无空格开头)
```
````

