```js
let obj = new Object() // => obj 叫变量, 它的值是内存地址(栈内存), 地址住着空对象(堆内存)

obj.__proto__ //=> obj变量下的__proto__属性, 值是内存地址,地址住着对象,__proto__的值放的对象称之为原型

Object.prototype//Object变量下的prototype属性,值是内存地址,地址住着对象

obj.__proto__ ==Object.prototype

//obj 是 Object 创建的 Object就会把prototype放到obj的__proto__上

//所以 obj.__proto__  ===  Object.prototype 因为他们内存地址相同,住的是同一个对象

//得出 Object.prototype 是 obj的原型 通过 obj.__proto__获取
```