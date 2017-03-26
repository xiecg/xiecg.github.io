---
title: 你不知道的 JavaScript 中卷笔记
date: 2017-03-21 22:37:17
tags:
---

#### 1：类型

内置类型：`null`, `undefined`, `boolean`, `number`,`string`, `object`, 还有 es6 的 `symbol`。

变量是没有类型的，变量的值才有类型。

#### 2：值

函数传参是按值传递还是引用传递 ？

基本类型是按值传递的，`object` 是按共享传递的。

扩展阅读：[js-call-by-sharing](http://bosn.me/js/js-call-by-sharing/)

基本类型定义了几个特殊的值：

`null` 类型只有一个值是 `null`，`undefined` 类型也只有一个值是 `undefined`

数字类型也有几个特殊的值：包含 `NaN`，`+Infinity`，`-Infinity`，`-0` 。

扩展阅读：[Equality_comparisons_and_sameness](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Equality_comparisons_and_sameness)

#### 3： 原生函数

JavaScript 中的基本数据类型提供了封装对象，称为原生函数（ `String`, `Object`, `Number` 等）。

对于基本类型值，比如 `var text = 'text';` 要访问 `text` 的 `length` 方法，引擎会自动对这些值进行封装，就是对应的`封装对象`来包装他。

#### 4：强制类型转换

###### 4-1:   ~ 运算符

```JavaScript
~42;	// -(42+1) ==> 43
```

在 `-(x+1)` 中 `x` 如果为 `-1` 时，~ 和一些数字值在一起就会返回假值 `0`， 其他情况都是返回 `真值`。

`-1` 是一个 “哨位值”，`-1` 表示失败，大于等于 `0` 表示成功。

`indexOf`  遵循这一惯例：

```JavaScript
var a = 'Hello World';
if ( a.indexOf( 'lo' ) >= 0 ) { ... } 	// true， 找到匹配
if ( a.indexOf( 'lo' ) != -1 ) { ... } 	// true， 找到匹配
if ( a.indexOf( 'lo' ) < 0 ) { ... }	// true, 没有找到匹配
if ( a.indexOf( 'lo' ) == -1 ) { ... }	// true，没有找到匹配
```
如果换成 `~` 运算符会更简洁：

```JavaScript
var a = 'Hello World';
console.log( ~a.indexOf( 'lo' ) );	// -4, 真值
if ( ~a.indexOf('lo') ) { ... } 	// true, 找到匹配
console.log( ~a.indexOf('ol') );	// 0, 假值
if ( !~a.indexOf('ol') ) { ... };	// true, 没有找到匹配
```

字位截取：

```JavaScript
Math.floor( -49.6 );	// -50
~~-49.6;				// -49
```

