# JS 函数的执行时机
## for 与 setTimeout
首先看下面代码
```js
//第一次
for(var i = 0; i<3; i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}
//打印  3,3,3
```
我们可以得出结论,先是`for`语句循环了3遍,再执行了3遍`console.log`,这样就能解释为什么三遍打印都是`i`最后的值,那么再看下面代码
```js
//第二次
for(let i = 0; i<3; i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}
//打印  0,1,2
```
为什么`let`会影响结果,真的是因为`let`改变了执行机了吗,继续看
```js
//第三次
let i ;
for( i = 0 ; i<3; i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}
//打印  3,3,3
```
我们把`let`和`for`脱离开,又回到了第一次的结果,说明只有当`let`和`for`组合成一个语句的时候,会触发一些隐藏机制,那我就着重研究第二次的代码
```js
//第二次
for(let i = 0; i<3; i++){
    console,log(`真实的i:${i}`)
    setTimeout(()=>{
        console.log(i)
    },1000)
}
//打印  真实的i:0 ,真实的i:1 ,真实的i:2  过1秒 0,1,2
```
这我们就明白了,真实的`i`已经变成3了,但是`setTimeout`又能输出之前已经不存在的`i`,说明`setTimeout`输出的`i`其实是真实`i`的一份拷贝,循环每执行一次,那么js会对当前`i`进行一次拷贝,提供给`setTimeout`使用,这就是`let`和`for`同时存在的隐藏机制

## 那怎样真正做到循环延迟呢?
我们可以用递归实现
```js
function myfor(i, frequency, fn) {
    if (i < frequency) {
        setTimeout(() => {
            fn(i)
            myfor(++i, frequency, fn)
        }, 100)
    }
}
myfor(0, 5, (i) => {
    console.log(i)
})
// 打印 0,1,2,3,4
```
这样每次循环都能执行指定自己提供的函数(循环体),但是递归也是有限制的,递进过程中需要占用栈内存,无限递归就会导致栈溢出,一般次数1w以下最佳(不同浏览器内核上限不同)
