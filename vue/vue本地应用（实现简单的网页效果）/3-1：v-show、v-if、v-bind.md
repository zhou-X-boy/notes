### 1：[v-show指令](https://cn.vuejs.org/v2/api/#v-show)

###### 					1）根据表达值的真假，切换元素的显示和隐藏

###### 					2）根据布尔值切换(true显示,false隐藏)

###### 					3）原理是修改元素的display样式，实现显示和隐藏

###### 					4）指令后面的值，最终都会被解析为布尔值，也就是true和false

```html
<div id="app">
    <a herf=" " v-show="false"></a>
    <!--如果里面的结果为true则显示，否则就隐藏-->
    <button v-show="age>18"></button>
    <input type="button" value="点击切换显示状态" @click="changeShow">
    <img src=" " v-show="isShow">
</div>
<script>
	var vm = new Vue({
        el:"#app",
        data:{
            isShow:true,
            age:16
        },
        methods:{
            changeShow:function(){
                this.show = !this.show
            }
        }
    })
</script>
```

### 2：[v-if指令](https://cn.vuejs.org/v2/api/#v-if)

###### 		1）根据表达值的真假，切换元素的显示和隐藏

###### 		2）本质是操纵Dom元素来切换，移除或者是添加

###### 		3）根据布尔值切换(true显示,false隐藏)

###### 		4）表达式的值为true，元素存在于dom树中；为false，元素从dom树中移除

```html
<div id="app">
    <input type="button" value="点击切换显示隐藏" @click="changeIsShow"> 
    <p v-if="isShow">vue</p>
   	<p v-if="age>20">vue</p>
</div>
<script>
	var vm = new Vue({
        el:"#app",
        data:{
            isShow:true,
            age:18
        },
        methods:{
           changeIsShow:function(){
               this.isShow = !this.isShow
           } 
        }
    })
</script>
```

### 3：[v-bind指令](https://cn.vuejs.org/v2/api/#v-bind)

###### 				1）设置元素的属性（比如src，class，title都写在元素的内部）

###### 				2）语法 v-bind:属性名 = 表达式   简写 （ :属性名 = 表达式）

```html
<head>
    <style>
        .active{
            border:1px solid red;
        }
    </style>
</head>
<div id="app">
    <img v-bind:src="imgSrc" alt="">
    <img v-bind:title="imgTiele" alt="">
    <!--拼接-->
    <img v-bind:title="imgTiele + 'vue' " alt="">
    <!--三元表达式-->
    <img v-bind:class="isActive ? 'active' : ' ' " 
         v-bind:src="imgSrc"
         alt=""  
         @click="changeBind">
    <!--简写-->
    <img :class="{'active':isActive}"
         :src="imgSrc"
         alt="" 
         @click="changeBind">
</div>
<script>
	var vm = new Vue({
        el:"#app",
        dtat:{
            imgSrc:"图片地址",
            imgTitle:"vue",
            isActive:true
        },
        methods:{
            changeBind:{
                this.isActive = !this.isActive
            }
        }
    })
</script>
```

