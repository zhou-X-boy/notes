### 1：axios结合vue开发网络应用

​		1）axio回到函数中的this已经改变，无法访问data中的数据

​		2）把this保存起来，回调函数中直接使用保存的this即可

![image-20201005110120263](C:\Users\25798\AppData\Roaming\Typora\typora-user-images\image-20201005110120263.png)

```html
<head>
    <!--导入vue的在线包-->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
     <!--导入axios的在线包-->
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
</head>
<body>
    <div id="app">
        <input type="button" value="随机获取笑话" @ckick="getJoke">
        <p>{{joke}}</p>
    </div>
    <script>
    	var vm = new Vue({
            el:"#app",
            data:{
                joke:"点击随机获取笑话"
            },
            methods:{
                getJoke:function(){
                    //因为在下面的回调函数内部使用this会访问不到data数据，所以将this固定给另外一个值，这样就能使用
                    var that = this;
                    axios.get("https://autumnfish.cn/api/joke").then(function(response){
                        console.log(response);//打印出获取到的信息
                        console.log(response.data);//获取需要的信息并打印
                        that.joke = response.data //将获取到的信息赋值给data里的joke
                    },function(err){
                        console.log("错误信息："+err);
                    })
                }
            }
        })
    </script>
</body>
```

