# JS 对象基本用法
## 声明对象的两种语法
```js
// 第一种
let obj_1 = {}

// 第二种 
let obj_2 = new Object()
```
## 如何删除对象的属性
```js
let obj = {name:"张三"}
delete obj.name
```
## 如何查看对象的属性
```js
let obj = {name:"张三"}
let myName = "name"
// 三种查看方式
obj.name 
obj["name"] 
obj[myName] 
```
## 如何修改或增加对象的属性
```js
let obj = {name:"张三"}
obj.name = "李四"
obj.age = 18
console.log(obj) // {name:"李四":age:18}
```
## 'name' in obj和obj.hasOwnProperty('name') 的区别
两者都能表示`name`是否为`obj`的属性
```js
var obj = {name:"张三"}
console.log('name' in obj)//true
console.log(obj.hasOwnProperty('name'))//true

//尝试一下toString
console.log('toString' in obj)//true
console.log(obj.hasOwnProperty('toString'))//false
```
**由此可知**

* `hasOwnProperty`表示对象自身属性中是否具有指定的属性(键)
* `in`表示`hasOwnProperty`基础上,再包括原型属性
