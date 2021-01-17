# 理解Vue数据响应式原理

## 什么是数据响应式
>Vue 最独特的特性之一 `数据响应式`,是其非侵入性的响应式系统。数据模型仅仅是普通的 JavaScript 对象。而当你修改它们时，视图会进行更新

## 如何实现响应式
>当你把一个普通的 JavaScript 对象传入 Vue 实例作为 `data` 选项，Vue 将遍历此对象所有的 property，并使用 `Object.defineProperty` 把这些 property 全部转为 `getter/setter`。

**以上均为官方解释,如何更接地气的深入理解,请看下文**

#### 例1
```js
const boy = { age: 18 }
console.log(boy) // {age:18,_proto_:Object}
```
正常情况我们声明一个对象,对象内只有它的成员和_proto_

#### 例2
那我们将数据交给Vue管理将会怎样
```js
const boy = { age: 18 }

const vm = new Vue({
    data: boy
}).$mount("#app");
        
setTimeout(() => {
    console.log(boy) // {age:18,get age:fn,set age:fn}
})
```
此时打印出来的对象比之前多了`get age`和`set age`,那么就表示我们通过`boy.age`去获取和修改都是要通过这两个函数的,但很明显这是Vue后来添加进去的,说明我们的原始数据被'劫持'了

**那么重点来了,Vue的行为是想让我们通过它来修改数据,不希望我们直接修改原始数据,下面来一步一步探讨**

#### 例3

如何用`Object.defineProperty`来监听数据
```js
const boy = {}
let $age = 18

Object.defineProperty(boy, 'age', {
    get() {
        return $age
    },
    set(value) {
        if (value < 0) return
        $age = value
    }
})

boy.age = 10
console.log(boy.age) // 10
boy.age = -1
console.log(boy.age) // 10
$age = -1
console.log(boy.age) // -1
```
上述方式可知Vue是如何对数据进行修改的,通过`boy.age`访问的其实是`$age`,所以直接修改`$age`能绕过set的监听,所以需要使用代理并且监听原数据

#### 例4

```js
const boy = { age: 18 }
const proxy_boy = proxy({ data: boy })

function proxy({ data }) {
    let age = data.age //原对像
    Object.defineProperty(data, 'age', {
        get() {
            return age
        },
        set(value) {
            if (value < 0) return
            age = value
        }
    })

    const obj = {} // 代理对象
    Object.defineProperty(obj, 'age', {
        get() {
            return data.age
        },
        set(value) {
            data.age = value
        }
    })
    return obj
}

proxy_boy.age = 10
console.log(proxy_boy.age) //10
proxy_boy.age = -1
console.log(proxy_boy.age) //10
boy.age = -1
console.log(proxy_boy.age) //10
```
上述代码无论是修改`proxy_boy.age`还是`boy.age`, 都能被监听到,Vue就能保证一定可以~~中间商赚差价~~监听到数据变化并更新视图

### 如果我们把函数名换一下....
```js
const proxy_boy = proxy({ data: boy })
// 换成
const vm = Vue({data:boy})
// 获取年龄
vm.age
```
是不是不知不觉就手写了数据响应式


