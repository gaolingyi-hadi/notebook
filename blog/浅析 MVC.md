# 浅析 MVC什么是MVC？
## MVC 三个对象分别做什么?
M是modal(数据模型)的简称,它是用于操作所有数据
```js
const m = {
    data: {
        num: 0
    },
    set() {
        //操作
    }
}
```

V是view(视图)的简称,它是用于负责所有UI界面
```js
const v = {
    el: null,
    init() {
        //初始化容器
    },
    render() {
        //渲染
    }
}
```
C是controller（控制器）的简称,它负责其他
```js
const c = {
    init(container) {
        //初始化
        v.init().render()      
    },
    autoBindEvents(){
        // 绑定事件 监听事件
    }
}
```
## EventBus中的API
有神三个常用api 分别是：on、trigger、off;

```
on(name,()=>{
    //监听变化,更新数据
})

trigger(name,()=>{
    //主动触发事件
})

off(name,()=>{
    //关闭监听
})
```

## 表驱动编程
表驱动方法是一种使你可以在表中查找信息,而不必用很多的逻辑语句（if或Case）来把它们找出来的方法.

## 如何理解模块化
模块提供使用接口,彼此之间互不影响,每个模块都是实现某一特定的功能.抽离后的模块能更好维护

每个模块还可以使用不同的技术栈,模块内部引用是独立的