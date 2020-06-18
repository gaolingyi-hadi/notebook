# JavaScript语法

## 什么是表达式和语句
    表达:式产生一个值，可能是运算、函数调用
    语句:由";"分隔的句子，用一句话表示一个行为
## 标识符的规则
* 首字母必须是字母、下划线（_）或美元符号（$），不能是数字
* 除首字母外，其他字符可以是字母、数字、下划线或美元符号（$）
* 不能是关键字或保留字(不同语言不同关键字)
## if else 语句
    当指定条件为真，if 语句会执行一段语句。如果条件为假，则执行另一段语句

```js
if (true) {
    console.log("条件为真")
} else {
    console.log("条件为假")
}
```
## while for 语句
  循环语句可以在某个条件表达式为真的前提下，循环执行指定的一段代码，直到那个表达式不为真时结束循环
```js
while (n < 3) {
  n++;
}
```
  
```js
for (let i = 1; i < 9; i++) {
  console.log(`循环了${i}次`)
}
```
## break continue 语句
    在循环体重加入 `continue` ，那会结束本次循环，直接进入下次循环。若加入`break`那么会结束循环循环语句，不再循环
## label
    标记语句`label`可以和 break 或 continue 语句一起使用
    当存在循环嵌套，`break` `continue`只能对离自身最近循环语句生效
```js
forlabel1:
for (let i = 0; i < 5; i++) {
    forlabel2:
    for(let j = 0; j < 5; j++) {
        if(i === 2 && j === 2){
            break forlabel1;
            //这样就直接跳出整个循环了
        }
    }
}
```