### 1： 什么是生命周期：从Vue实例创建、运行、到销毁期间，总是伴随着各种各样的事件，这些事件，统称为生命周期！

### 3：生命周期钩子：就是生命周期事件的别名；

### 4： 生命周期钩子 = 生命周期函数 = 生命周期事件

### 5：主要的生命周期函数分类：

- [ ] ##### 	创建期间的生命周期函数：

  > ​	1）beforeCreate：实例刚在内存中被创建出来，此时，还没有初始化好 data 和 methods 属性
  > ​    2）created：实例已经在内存中创建OK，此时 data 和 methods 已经创建OK，此时还没有开始 编译模板
  >    3） beforeMount：此时已经完成了模板的编译，但是还没有挂载到页面中
  >    4） mounted：此时，已经将编译好的模板，挂载到了页面指定的容器中显示

- [ ] #####  运行期间的生命周期函数：

  > 5）beforeUpdate：状态更新之前执行此函数， 此时 data 中的状态值是最新的，但是界面上显示的 数据还是旧的，因为此时还没有开始重新渲染DOM节点
  > 6）updated：实例更新完毕之后调用此函数，此时 data 中的状态值 和 界面上显示的数据，都已经完成了更新，界面已经被重新渲染好了！

- [ ] ##### 销毁期间的生命周期函数：

  > 7）beforeDestroy：实例销毁之前调用。在这一步，实例仍然完全可用。
  > 8）destroyed：Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。 

  ------

  ------

  

> ##### 创建前： beforeCreate
>
> 对应的钩子函数为beforeCreate。此阶段为实例初始化之后，此时的数据观察和事件机制都未形成，不能获得DOM节点。

> ##### 创建： created
>
> 对应的钩子函数为created。在这个阶段vue实例已经创建，仍然不能获取DOM元素。

> ##### 载入后： mounted
>
> 对应的钩子函数是beforeMount，在这一阶段，我们虽然依然得不到具体的DOM元素，但vue挂载的根节点已经创建，下面vue对DOM的操作将围绕这个根元素继续进行；beforeMount这个阶段是过渡性的，一般一个项目只能用到一两次。

> ##### 更新前： beforeUpdate
>
> 对应的钩子函数是beforeUpdate。在这一阶段，vue遵循数据驱动DOM的原则。beforeUpdate函数在数据更新后虽然没立即更新数据，但是DOM中的数据会改变，这是Vue双向数据绑定的作用。

> ##### 更新：updated
>
> 对应的钩子函数是updated。在这一阶段DOM会和更改过的内容同步。

> ##### 销毁前： beforeDestroy
>
> 对应的钩子函数是beforeDestroy。在上一阶段Vue已经成功的通过数据驱动DOM更新，当我们不再需要vue操纵DOM时，就要销毁Vue,也就是清除vue实例与DOM的关联，调用destroy方法可以销毁当前组件。在销毁前，会触发beforeDestroy钩子函数。

> ##### 销毁 destroy
>
> 对应的钩子函数是destroyed。在销毁后，会触发destroyed钩子函数。

![Vue生命周期](D:\text\vue\Vue生命周期.png)

```html

<!DOCTYPE html>
<html lang="en">
 
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <script type="text/javascript" src="../lib/vue-2.4.0.js" ></script>
  <link rel="stylesheet" href="../lib/bootstrap-3.3.7.css"></link>
</head>
 
<body>
  <div id="app">
    <input type="button" value="修改msg" @click="msg='No'">
    <h3 id="h3">{{ msg }}</h3>
   </div>
</body>
```

> ```html
> <script>
> // 创建 Vue 实例，得到 ViewModel
>     var vm = new Vue({
>       el: '#app',
>       data: {
>         msg: 'ok'
>       },
>       methods: {
>         show() {
>           console.log('执行了show方法')
>         }
>       },
> ```
>
> ##### 这是我们遇到的第一个生命周期函数，表示实例完全被创建出来之前，会执行它
>
> ```javascript
> beforeCreate:function() { 
>           // console.log(this.msg)
>           // this.show()
>           // 注意： 在 beforeCreate 生命周期函数执行的时候，data 和 methods 中的 数据都还没有没初始化
>       },
> ```



> ##### 这是遇到的第二个生命周期函数
>
> ```javascript
>  created:function() { 
>         // console.log(this.msg)
>         // this.show()
>         //  在 created 中，data 和 methods 都已经被初始化好了！
>         // 如果要调用 methods 中的方法，或者操作 data 中的数据，最早，只能在 created 中操作
>       },
> ```



> ##### 这是遇到的第3个生命周期函数，表示 模板已经在内存中编辑完成了，但是尚未把 模板渲染到 页面中  
>
> ```javascript
> beforeMount:function() {
>         // console.log(document.getElementById('h3').innerText)
>         // 在 beforeMount 执行的时候，页面中的元素，还没有被真正替换过来，只是之前写的一些模板字符串
>       },
> ```



> ##### 这是遇到的第4个生命周期函数，表示，内存中的模板，已经真实的挂载到了页面中，用户已经可以看到渲染好的页面了
>
> ```javascript
> mounted:function() {
>         // console.log(document.getElementById('h3').innerText)
>         // 注意： mounted 是 实例创建期间的最后一个生命周期函数，当执行完 mounted 就表示，实例已经被完全创建好了，此时，如果没有其它操作的话，这个实例，就静静的 躺在我们的内存中，一动不动
>       },
> ```

>  接下来的是运行中的两个事件
>
> ##### 当执行 beforeUpdate 的时候，页面中的显示的数据，还是旧的，此时 data 数据是最新的，页面尚未和 最新的数据保持同步
>
> ```javascript
>  beforeUpdate:function() { // 这时候，表示 我们的界面还没有被更新【数据被更新了吗？  数据肯定被更新了】
>         /* console.log('界面上元素的内容：' + document.getElementById('h3').innerText)
>         console.log('data 中的 msg 数据是：' + this.msg) */
>         // 得出结论： 当执行 beforeUpdate 的时候，页面中的显示的数据，还是旧的，此时 data 数据是最新的，页面尚未和 最新的数据保持同步
>       },
> ```
>
> ##### updated 事件执行的时候，页面和 data 数据已经保持同步了，都是最新的
>
> ```javascript
>   updated:function() {
>         console.log('界面上元素的内容：' + document.getElementById('h3').innerText)
>         console.log('data 中的 msg 数据是：' + this.msg)
>         // updated 事件执行的时候，页面和 data 数据已经保持同步了，都是最新的
>       }
> ```



> ##### 在上一阶段Vue已经成功的通过数据驱动DOM更新，当我们不再需要vue操纵DOM时，就要销毁Vue,也就是清除vue实例与DOM的关联，调用destroy方法可以销毁当前组件。在销毁前，会触发beforeDestroy钩子函数。
>
> ```javascript
> beforeDestroy :function() {
>                 
>             },
> ```



> 在销毁后，会触发destroyed钩子函数。
>
> ```javascript
>  destroyed: function () {
>                 
>            }
> ```



完整的代码


```html
<script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        msg: 'ok'
      },
      methods: {
        show() {
          console.log('执行了show方法')
        }
      },
        
      beforeCreate:function() { // 这是我们遇到的第一个生命周期函数，表示实例完全被创建出来之前，会执行它
          // console.log(this.msg)
          // this.show()
          // 注意： 在 beforeCreate 生命周期函数执行的时候，data 和 methods 中的 数据都还没有没初始化
      },
        
      created:function() { // 这是遇到的第二个生命周期函数
        // console.log(this.msg)
        // this.show()
        //  在 created 中，data 和 methods 都已经被初始化好了！
        // 如果要调用 methods 中的方法，或者操作 data 中的数据，最早，只能在 created 中操作
      },
      
      beforeMount:function() { // 这是遇到的第3个生命周期函数，表示 模板已经在内存中编辑完成了，但是尚未把 模板渲染到 页面中
        // console.log(document.getElementById('h3').innerText)
        // 在 beforeMount 执行的时候，页面中的元素，还没有被真正替换过来，只是之前写的一些模板字符串
      },
      mounted:function() { // 这是遇到的第4个生命周期函数，表示，内存中的模板，已经真实的挂载到了页面中，用户已经可以看到渲染好的页面了
        // console.log(document.getElementById('h3').innerText)
        // 注意： mounted 是 实例创建期间的最后一个生命周期函数，当执行完 mounted 就表示，实例已经被完全创建好了，此时，如果没有其它操作的话，这个实例，就静静的 躺在我们的内存中，一动不动
      },
 
 
      // 接下来的是运行中的两个事件
      beforeUpdate:function() { // 这时候，表示 我们的界面还没有被更新【数据被更新了吗？  数据肯定被更新了】
        /* console.log('界面上元素的内容：' + document.getElementById('h3').innerText)
        console.log('data 中的 msg 数据是：' + this.msg) */
        // 得出结论： 当执行 beforeUpdate 的时候，页面中的显示的数据，还是旧的，此时 data 数据是最新的，页面尚未和 最新的数据保持同步
      },
      update:functiond() {
        console.log('界面上元素的内容：' + document.getElementById('h3').innerText)
        console.log('data 中的 msg 数据是：' + this.msg)
        // updated 事件执行的时候，页面和 data 数据已经保持同步了，都是最新的
      }
    });
</script>
```