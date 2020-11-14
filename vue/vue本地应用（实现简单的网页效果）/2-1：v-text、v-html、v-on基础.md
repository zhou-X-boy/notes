### 1：[v-text指令](https://cn.vuejs.org/v2/api/#v-text)

###### 		1）v-text指令的作用是：设置标签的内容（textContent）

###### 		2）默认写法会替换全部内容，使用差值表达式{{}}可以替换指定内容

###### 		3）内容支持写表达式

```html
<div id="app">
   <p v-text="message">vue</p>
    <!--插值表达式-->
    <p>
       {{message}} 
    </p>
    <!--拼接-->
    <p v-text="message + 'vue'"></p>
    <p>
        {{message + "vue"}}
    </p>
</div>
<script>
	var vm = new Vue({
        el:"#app",
        data:{
            message:"hello vue"
        }
    })
</script>
```

### 2：[v-html指令](https://cn.vuejs.org/v2/api/#v-html)

###### 		1）设置元素的innerHTML

###### 		2）内容中有html结构，会被解析成标签

```html
<div id="app">
    <p v-html="content"></p>
</div>
<script>
	var vm = new Vue({
        el: "#app",
        data: {
            content:"<a href='https://www.baidu.com'>vue</a>"
        }
    })
</script>
```

### 3：[v-on指令基础](https://cn.vuejs.org/v2/api/#v-on)

###### 		1）为元素绑定事件

#####      		（1） 鼠标点击事件 v-on:click="方法名"     简写  @clock="方法名"

##### 			 （2）鼠标移入事件 v-on:mouseenter="方法名"     简写  @mouseenter="方法名"

##### 			 （3）鼠标双击事件 v-on:dblclick="方法名"       简写    @dblclick="方法名"  

###### 		2）事件名不需要写on

###### 		3）绑定的方法定义在methods中

```html
<div id="app">
    <a @click="a">鼠标点击事件绑定</a>
    <input type="button" value="鼠标移入事件绑定" @mouseenter="b">
    <button @dblclick="c">鼠标双击事件绑定</button>
</div>
<script>
	var vm = new Vue({
        el:"#app",
        //数据
        data:{
            
        },
        //方法
        methods:{
           	a:function(){},
        	b:function(){},
            c:function(){}
        }
    })
</script>
```

##### 		更改数据，通过 this.数据名 的方法获取到数据

```html
<div id="app">
    <a @click="changeName">鼠标点击事件绑定</a>
    <input type="button" value="鼠标移入事件绑定" @mouseenter="changeName">
    <button @dblclick="changeName">鼠标双击事件绑定</button>
</div>
<script>
	var vm = new Vue({
        el:"#app",
        //数据
        data:{
            name:"z"
        },
        //方法
        methods:{
           	changeName:function(){
                //this.name=this.name+"w"
                this.name += "w"
            }
        }
    })
</script>
```

