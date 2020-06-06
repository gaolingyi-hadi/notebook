# HTML常用标签

## a标签

写法是 `<a href="https://baidu.com">百度</a>` 

|主要属性|常用值|
|:-|:-|
|`href`|`URL`,`javascript:;`,`#`,`#id`|
|`target`|`_blank`在新窗口打开|

`<a>`标签经常用来做超链接跳转

## img标签

写法是 `<img src="" alt="">` 

|主要属性|常用值|
|:-|:-|
|`src`|`URL`本地连接或者网络图片|
|`alt`|`String`图片加载失败的描述文字|
 
`<img>`是用来展示图片的标签

## table标签

写法是 
``` html
<table>
    <thead>
      <tr>
        <th></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td></td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td></td>
      </tr>
    </tfoot>
</table>
```
`<table></table>`用来声明表格开始与结束.

`<th></th>`用来设置标题栏位.

`<tr></tr>`用来设置表格的行.

`<td></td>`用来设置数据栏位.

`<thead> <tbody> <tfoot>`平时会自动补全, 顺序调换也不受影响

`<table>`标签可以很轻易的制作出一个表格

## form标签

写法是 `<form></form>`

`<form>`标签基本不是单独使用的,里面需要嵌套`<input>`、` <button>`来提交表单请求服务器的