### 1：[axios](https://github.com/axios/axios)是一个功能强大的网络请求库

### 2：导包

```html
<!--axios的在线地址-->
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

### 3：请求方法

##### get请求

```javascript
axios.get(地址).then(function(response){},function(err){});
//地址就是文档提供的接口地址
//response 指服务器响应的内容  err是返回的错误的信息
//如果需要传递参数，在地址后面接上  使用?分隔 key=value&key2=value2
axios.get("请求地址?key=value & key2=value2").then(function(response){},function(err){});
```

##### post请求

```javascript
axios.post("请求地址",{key=value,key2=value2}).then(function(response){},function(err){});
//key由接口文档提供，value是具体要传递的数据
```

### 4：接口（百度查找）

![image-20201005103412511](C:\Users\25798\AppData\Roaming\Typora\typora-user-images\image-20201005103412511.png)

### 5：例子

```html
<head>
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
</head>
<body>
    <input type="button" value="get请求方法" class="get">
    <input type="button" value="post请求方法" class="post">
    <script>
    /*
    	接口1：随机笑话
    	请求地址：https://autumnfish.cn/api/joke/list
    	请求方法：get
    	请求参数：num（笑话条数，数字）
    	响应内容：随机笑话
    */
        //通过document.querySelector(".get")获取到class为get的按钮
        document.querySelector(".get").onclick = function(){
            axios.get("https://autumnfish.cn/api/joke/list?num=3").then(function(response){
                console.log(response);//打印结果在下方
            },function(err){
                console.log("错误信息："+err)
            })
        }
     /*
    	接口2：用户注册
    	请求地址：https://autumnfish.cn/api/user/reg
    	请求方法：post
    	请求参数：username（用户名，字符串）
    	响应内容：注册成功或失败
    */
        document.querySelectot(".post").onclick = function(){
            axios.post("https://autumnfish.cn/api/user/reg",{username:"jack"}).then(function(response){
                console.log(response);//打印结果在下方
            },function(err){
                console.log("错误信息："+err)
            })
        }
    </script>
</body>
```

##### get方法 console.log(response);打印出得结果，我们需要就是data里面的数据

![image-20201005104636757](C:\Users\25798\AppData\Roaming\Typora\typora-user-images\image-20201005104636757.png)

##### post方法 console.log(response);打印出得结果，我们需要就是data里面的数据

![image-20201005105429371](C:\Users\25798\AppData\Roaming\Typora\typora-user-images\image-20201005105429371.png)