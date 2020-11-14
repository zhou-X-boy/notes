###### 1：列表数据使用数组保存

###### 2：v-bind指令设置元素属性

###### 3：v-show和v-if都可以切换元素显示与隐藏，频繁切换使用v-show

```html
<div id="app">
    <!--v-show为true就显示 为false就隐藏-->
   <a @click="add"  v-show="index != 0">上一张</a>
   <img :src="imgArr[0]">
   <a @click="sub"  v-show="index < imgArr.length-1">下一张</a>
</div>
<script>
	var vm = new Vue({
        el:"#app",
        data:{
            imgArr: ["图片地址","图片地址","图片地址"],
            index: 0
        },
        methods:{
            add:function(){
                this.index --
            },
            sub:function(){
                this.index ++
            }
        }
    })
</script>
```

