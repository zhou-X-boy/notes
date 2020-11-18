# vue-cli3/4脚手架搭建的项目

> 在babel.config.js文件中加入
>
> ```javascript
> "plugins": [
>   [
>     "component",
>     {
>       "libraryName": "mint-ui",
>       "style": true
>     },
>     "mint-ui"
>   ]
> ]
> ```

> 在项目入口文件中引入mint-ui组件
>
> ```javascript
> import Mint from 'mint-ui'
> import 'mint-ui/lib/style.css'
> ```

> 全局使用
>
> ```javascript
> Vue.use(MInt);
> ```

> 在需要使用mint-ui组件的地方，直接查看官方文档使用相关的组件