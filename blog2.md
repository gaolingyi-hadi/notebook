# CSS 盒模型是什么?

就是`box-sizing`的属性值
## 值为content-box时
设置`width`时不包含`padding`和`border`,

实际展示的宽度为`border`+ `padding`+`width`,所以模型往往会比预想中的宽

## 值为border-box时
设置`width`时包含`padding`和`border`,
实际展示的宽度为 `border`+ `padding`+`width`,**但是**他们之和就等于设置时的宽度

换句话说`width:100px`那么就是`border`+ `padding`+`width`之和等于`100px`