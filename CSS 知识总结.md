# CSS 知识总结

## 浏览器渲染原理

1. HTML字符串描述了一个页面的结构，解析HTML生成DOM树

1. 解析CSS产生CSS规则树,与DOM树相似

1. Javascript脚本文件加载后，通过 DOM API 和 CSSOM API 操作DOM Tree 和 CSS Rule Tree
1. Attachment 合成 DOM Tree 和 CSS Rule Tree

1. Layout布局操作空间布局

1. Paint绘制画面

1. Compose合成层叠关系

## CSS 动画的两种做法

1. `transition`属性,可以将其他属性有过程的变化,这个过程就生成了动画
1. `animation` 属性,可以自定义设置动画的关键帧,更加灵活

## CSS选择器优先级权值
1. 继承0.1    
2. 标签选择器 1    
3. 类选择器 10    
3. ID选择符器 100   
4. 内联样式 1000
1. `!important`最大

所以`#id`能覆盖`.class`

权值相同时,后定义的生效

尽量避免使用`!important`,宁愿用多个`.class`