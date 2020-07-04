# jQuery的使用方式

jQuer是前端很老的技术,在2020年,我认为即使项目用不上,也要学习它的思想,它产生的价值不仅仅是开发效率,下面就介绍jQuer使用户方式

[TOC]
## 获取元素
jQuery的的选择器可以容易的找到节点对象,并提供丰富的AIP提供操作

通过scc选择器
```js
$(document) //选择整个文档对象

$('#id') //通过id获得对象

$('div.class') // 通过css获得对象

$('input[name=first]') //通过属性获得对象
```
[jQuery自己也有一套选择方式](https://api.jquery.com/category/selectors/)

## 修改元素的属性
```js
$('.class').html() //取出或设置html内容

$('.class').text() //取出或设置text内容

$('.class').attr() //取出或设置某个属性的值

$('.class').width() //取出或设置某个元素的宽度

$('.class').height() //取出或设置某个元素的高度

$('.class').val() //取出某个表单元素的值
```
**温馨提示**: 如果结果集包含多个元素，那么赋值的时候，将对其中所有的元素赋值；取值的时候，则是只取出第一个元素的
## 创建元素
只需将html字符串传入构造函数即可
```js
　　$('<p>Hello</p>');

　　$('ul').append('<p>Hello</p>');
```
## 移动元素
假设我们选中了一个div元素，需要把它移动到p元素后面。

第一种方法是使用`.insertAfter()`，把div元素移动p元素后面：

`$('div').insertAfter($('p'));`

第二种方法是使用`.after()`，把p元素加到div元素前面：

`$('p').after($('div'));`
要注意的是函数返回值不同。第一种方法返回div元素，第二种方法返回p元素

再说说四对这种模式的操作方法

* `.insertAfter()`和`.after()`：在现存元素的外部，从后面插入元素

* `.insertBefore()`和`.before()`：在现存元素的外部，从前面插入元素

* `.appendTo()`和`.append()`：在现存元素的内部，从后面插入元素

* `.prependTo()`和`.prepend()`：在现存元素的内部，从前面插入元素

## 链式操作
jQuery的函数均返回一个jq对象,可以在一行代码中不间断操作
```js
$('div') //找到div元素
.find('h3') //选择其中的h3元素
.eq(2) //选择第3个h3元素
.html('Hello'); //将它的内容改为Hello
```
函数都在前一个返回值中调用

