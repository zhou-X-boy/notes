##### 1：v-on指令的作用是绑定事件，简写为@

##### 2：方法中通过this，关键字获取data中的数据

##### 3：v-text指令的作用是，设置元素的文本值，简写{{}}

```html
<div id="app">
    <button @click="add">
        +
    </button>
    <span>{{num}}</span>
    <button @click="sub">
        -
    </button>
</div>
<script>
	var vm = new Vue({
        el:"#app",
        data:{
            num:0
        },
        methods:{
            add:function(){
                //this.num = this.num+1
                this.num ++
            },
            sub:function(){
                if(this.num>0){
                    //this.num = this.num-1
                    this.num --
                }else{
                    alert("已经为最小值")
                }
             }
        }
    })
</script>
```

