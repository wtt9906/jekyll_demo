---
layout: page
title: 时间轴sample和random的canvas
---
#时间轴sample和random的canvas

##时间轴sample


今天在微博上看到 [年轻人的简历](http://www.koppt.me/resume/ "title") ,--哎，对比之下之前自己的html的简历真是太粗糙了。。。
而且这个小朋友还是华南师范大学，参加了广州亚运会的计算机志愿者。。。当时我在新奥特做实习，去广州的时候，那帮志愿者都用崇拜的眼光看我，如果这个小朋友也是当时之一，真是成长了不少哇~

觉得最后一个时间轴的效果，虽然颜色不太搭调，但是交互的效果挺好

于是就上网找，果然找到了[Lateral On-Scroll Sliding](http://tympanus.net/codrops/2011/12/05/lateral-on-scroll-sliding-with-jquery/ "title")原版，
下面是[demo](http://wtt9906.github.com/jekyll_demo/scrolltest.html "title")

##总结一下
###css部分

1. 在中间加竖线：配合：before和after要在制定元素前后插入DD，利用content:""
2. 虚线（before）和箭头（after）的位置top：50%，right:0/2%都是相对于ss-left的BFC里的50%
3. 箭头的画法
	1. 首先来看一下border的结构
![border](http://wtt9906.github.com/jekyll_demo/image/border.jpg),中间的白色正方形是盒子的内容部分，边长和边的宽度一致，四边的border用不同颜色区分
	2. 想象一下，中间区域无限小，长宽都是0px的时候，就剩下四种颜色的边，每条边看起来是个三角形
	3.	那么一个方向的边，就是一个箭头
	4.	那么是不是只留下一个边，就是一个箭头了呢，发现并不是那么顺利。先保留内容部分和一条边，我们发现出现的是两个一样大小的方块，![一条边](http://wtt9906.github.com/jekyll_demo/image/border1.jpg)因为只有一条边，但是增加一条相邻的边呢，两条边相交的地方，![两条边相交](http://wtt9906.github.com/jekyll_demo/image/border2.jpg)出现了一个我们想要的斜边，也有说，两条相交的border能出现一个斜边
	5.	接下来我们让内容部分消失![三条边并且没有内容](http://wtt9906.github.com/jekyll_demo/image/border3.jpg)
	6.	现在就明朗了，把上下部分的边，隐藏，就是我们要的箭头了
因为箭头出现在左边，箭头靠右，所以在右边设置一个10px的边，就是箭头的宽度，此时应该是一个长10px，宽5px的长方形，然后把上下border设为透明
4. 虚线 (border:dotted)补充一下，虚线和箭头，谁是before谁是after不重要，因为具体的位置是根据position：absolute和top,right指定的
5. 画圆
	1.	利用border-radius属性，指定4个方向边的弧度，四边50%就是一个圆
	2.	box-shadow:阴影类型(默认投影) X轴位移 Y轴位移 阴影大小 阴影扩展 阴影颜色,此处的阴影为两层，一个inset，一个投影,两个颜色
***
###js部分
1. 绑定了几个事件：resize.Scrolling,scroll.Scrolling（滑动滑动条）
2. defineViewport:当前事件是否发生在屏幕里
3. setViewportRows:把rows分成在屏幕内和屏幕外
3. $rowsViewport:当前屏幕里的rows，给这些rows加上ss-circle-deco的class
4. placeRows:屏幕外的rows,计算一个距离，左边和右边分别外扩,屏幕内的恢复到50%
5. 注意这里提到的几种高度 $row.offset().top,$window.height,$win.scrollTop()
***

##random的canvas
这就是随便瞎逛，逛到[尤小右空白的主页](http://www.evanyou.me/?from=inf&wvr=5&loc=infblog "title")，虽然什么都没有，但是主页的那条歪歪扭扭的彩带，不那么简单，从形状到颜色，都是动态生成的canvas（代码还是压缩过的，还是能看），我想做的贝塞尔曲线的canvas或许有可以借鉴的地方，于是我就copy下来

[canvas的demo](http://wtt9906.github.com/jekyll_demo/evanYou.html "title")

***

###另外一件事，今天去世贸天阶，运气好碰到有画插话的设计师，得了一副插画，回头放在博客的适当的位置
![我和fei的合影](http://wtt9906.github.com/jekyll_demo/image/feiandme.jpg)


