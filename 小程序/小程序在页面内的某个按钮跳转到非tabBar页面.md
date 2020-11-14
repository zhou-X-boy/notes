小程序在页面内的某个按钮跳转到非tabBar页面

1：在pages下创建一个文件夹opinion

![image-20200930174510835](D:\text\images\image-20200930174510835.png)

2：在该文件夹下创建opinion的page文件包，

3：在跳转页面(index.wxml)的js文件(index.js)下的`methods：{}`下添加一个`showOpinion()`函数，并在里面使用小程序自带的跳转页面的方法(小程序文档下的API下的路由内)，此处跳转页面是在当前页面下的某个按钮跳转到非tabBar页面，所以使用`wx.navigateTo()`方法,并在里面写入要跳转的地址![image-20200930174145905](D:\text\images\image-20200930174145905.png)

4：在需要点击跳转的按钮的最外层标签内添加点击事件`@click="showOpibion"`

![image-20200930174646887](D:\text\images\image-20200930174646887.png)

5:调式完后就可以实现效果