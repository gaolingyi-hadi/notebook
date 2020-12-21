# Vue两个版本的区别

## 名称区别
完整版 vue.js

非完整版 vue.runtime.js
 ## template 和 render 如何使用
 template使用方式
 ```html
 <template>
    <div id="app">      
        你好
   </div> 
</template>
<!-- 视图写在template里，完整版有compiler(编译器)用来解析视图 -->
 ```


render使用方式
```js
render(h){ 
    return h('div', '你好')
}
//非完整版没有compiler(编译器),只能通过render解析视图
```
 完整版使用