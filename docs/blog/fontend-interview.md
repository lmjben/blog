# 面试题

## 1、DOCTYPE 有什么用？

```text
文档模式：混杂模式和标准模式，主要印象css内容的呈现，在某些情况下也会影响js的执行。不同浏览器的怪异模式差别非常大
在 HTML 4.01 中，<!DOCTYPE> 声明引用 DTD，因为 HTML 4.01 基于 SGML。DTD 规定了标记语言的规则，这样浏览器才能正确地呈现内容。
HTML5 不基于 SGML，所以不需要引用 DTD。
```

## 如何提供包含多种语言内容的页面？

```text
当客户端向服务器发送 HTTP 请求时，通常会发送有关语言首选项的信息，比如使用Accept-Language请求头。如果替换语言存在，服务器可以利用该信息返回与之相匹配的 HTML 文档。返回的 HTML 文档还应在<html>标签中声明lang属性，比如<html lang="en">...</html>

在后台中，HTML 将包含i18n占位符和待以替换的内容，这些按照不同语言，以 YML 或 JSON 格式存储。然后，服务器将动态生成指定语言内容的 HTML 页面。整个过程通常需要借助后台框架实现。
```

## 请简述JavaScript中的this

- 在调用函数时使用new关键字，函数内的this是一个全新的对象。
- 如果apply、call或bind方法用于调用、创建一个函数，函数内的 this 就是作为参数传入这些方法的对象。
- 当函数作为对象里的方法被调用时，函数内的this是调用该函数的对象。比如当obj.method()被调用时，函数内的 this 将绑定到obj对象。
- 如果调用函数不符合上述规则，那么this的值指向全局对象（global object）。浏览器环境下this的值指向window对象，但是在严格模式下('use strict')，this的值为undefined。
- 如果符合上述多个规则，则较高的规则（1 号最高，4 号最低）将决定this的值。
- 如果该函数是 ES2015 中的箭头函数，将忽略上面的所有规则，this被设置为它被创建时的上下文。