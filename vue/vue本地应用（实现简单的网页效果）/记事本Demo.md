```html
<section id="todoapp">
	<!--输入框-->
    <header>
    	<input type="text" placeholder="请输入" v-model="inputValue" @keyup.enter="add">
   	</header>
    <!--列表区域-->
    <section>
    	<ul>
            <li v-for="(item,index) in list">
                <!--index,数组元素的下标-->
            	<span>{{index + 1}}</span>
                <!--item，获取到的数组元素-->
                <label>{{item}}</label>
                <!--给del方法传递一个参数，在上面通过v-for获取到的数组元素索引-->
                <button @click="del(index)">删除</button>
            </li>
        </ul>
    </section>
    <!--统计和清空-->
    <footer>
    	<p v-show="list.length != 0">{{list.length + 1}}</p>
     	<button @click="clear" v-if="list.length != 0">
            clear
        </button>
    </footer>
</section>
<script>
	var vm = new Vue({
        el:"#todoapp",
        data:{
            list:["a","b","c"],
            inputValue:"v-model绑定事件"
        },
        methods:{
            //给数组添加元素，使用push()方法，在数组最后面添加元素
            add:function(){
                this.list.push(this.inputValue)
            },
            //删除数组元素，使用splice(索引,删除个数)方法，在下面定义一个参数，接收上面传递过来的参数
            del:function(index){
                this.list.splice(index,1)
            },
            //清空数组元素，直接将数组变成空的数组就可
            clear:function(){
                this.list = []
            }
        }
    })
</script>
```

