### 1：[v-for指令](https://cn.vuejs.org/v2/api/#v-for)

###### 						1）根据数据生成列表结构

###### 						2）结合的类型有数组，对象，数字，字符串，迭代器等，数组经常跟v-for结合使用

###### 				3）语句 v-for=" (item,index) in  arr"

  				(1) item：遍历到的每一项，名字可修改

​				  (2) index：数组的索引，可修改，可不写

​				  (3) in :关键字，不可修改

​				  (4) arr ：要循环的数据名

###### 		4）item和index可结合其他指令一起使用，比如v-bind

###### 		5）数组长度的更新会同步到页面上，是响应式的

```html
<div id="app">
    <ul>
        <li v-if="item in arr">{{item}}</li>
    </ul>
    <ul>
        <li v-if="(item,index) in arr">
        	{{index}} {{item}}
        </li>
    </ul>
    <p v-if="item in person">
        {{item.name}}  {{item.age}}
    </p>
    <p v-if="item in person" :tilte="item.name">
        {{item.name}}  {{item.age}}
    </p>
    <button @click="add">添加元素</button>
    <button @click="remove">删除元素</button>
</div>
<script>
	var vm = new Vue({
        el:"#app",
        //数据
        data:{
            arr:["v","u","e"],
            person:[
                {name:"zhang",age:20},
                {name:"hong",age:19}
            ]
        },
        //方法
        methods:{
            add:function(){
                this.person.push({name:"qiu",age:20})//push()方法在数组后面添加新的元素
            },
            remove:function(){
                this.person.shift();//shift()方法，删除数组最前面的元素
            }
        }
    })
</script>
```

### 2：[v-on补充](https://cn.vuejs.org/v2/api/#v-on )

###### 				1）传递自定义参数，事件修饰符

###### 	    		2）修饰符

​		<img src="C:\Users\25798\AppData\Roaming\Typora\typora-user-images\image-20201004183125359.png" alt="image-20201004183125359" style="zoom:67%;" />

###### 3）事件绑定的方法写成函数调用的形式，可以传入自定义参数

###### 4）事件后面跟上  （.修饰符 ）  可以对事件进行限制

```html
<div id="app">
    <!--这里面的参数为需要传递给方法的参数-->
    <input type="button" value="点击传递自定义参数" @click="add('传到下面的方法的参数add1','传到下面的方法的参数add2')">
    <!--按键事件修饰符-->
    <input type="tetx" value="按下自定义的按键" @keyup.enter="removeKey">
</div>
<script>
	var vm = new Vue({
        el:"#app",
        data:{
            
        },
        methods:{
            add:function(add1,add2){//这里面的参数为前面点击事件传递过来的参数
                console.log(add1);//控制台输出：传到下面的方法的参数1
                console.log(add2);//控制台输出：传到下面的方法的参数
            },
            removeKey:function(){
                alert("按下自定义的按键弹出")
            }
        }
    })
</script>
```

### 3：[v-model](https://cn.vuejs.org/v2/api/#v-model)

###### 		1）便捷的获取和设置表单元素的值

###### 		2）双向数据绑定

###### 		3）绑定的数据会和表单元素相关联

```html
<div id="app">
    <!--v-mode进行了双向数据绑定，也就是说，修改input表单里的数据，data里的message也会被改变-->
    <input rype="text" v-model="message" @keyup.enter="getMessage">
</div>
<script>
	var vm = new Vue({
        el:"#app",
        data:{
            message:"vue"
        },
        methods:{
            getMessage:function(){
                alert(this.message);
            }
        }
    })
</script>
```

