## 1.
`npm i sass sass-loader -D`
## 2.
在vue.config.js中修改sass-loader的配置：
``` js
module.exports = {
  css: {
    loaderOptions: {
      sass: {
        implementation: require('sass'), // This line must in sass option
      },
    },
  }
};
```