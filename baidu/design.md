### transition 过渡

#### 语法

````
transition: transition-property transition-duration transition-timing-function transition-deplay
````

#### 解析

* transition-property：设置对象中的参与过渡的属性

    property | none | all

* transition-duration：设置对象过渡的持续时间。

* transition-timing-function：设置过渡效果的时间曲线

    默认值：ease

    贝塞尔曲线

    ease-in：本来没有速度，满满加速

    ease-out：本来有一定的速度，慢慢减速

    ease-in-out：开头结尾没有速度，先加速后减速

    linear：匀速运动

* transition-deplay：设置过渡效果何时开始

#### Ex

````
<a href="#" class="foo">Transition me!</a>

a.foo {
    padding: 5px 10px;
    background: #9c3;
    -webkit-transition: background .3s ease, color 0.2s linear;
    -moz-transition: background .3s ease, color 0.2s linear;
    -o-transition: background .3s ease, color 0.2s linear;
    transition: background .3s ease, color 0.2s linear;
}
a.foo:hover,
a.foo:focus {
    color: #030;
    background: #690;
}
````

### 2D转换

#### 语法

````
transform: translate(x, y) / rotate(n deg) / scale(x, y) / skew(x, y) / matrix(a, b, c, d, e, f)
transform-origin：x-axis y-axis z-axis
````

#### 解析

* 位移translate(x, y)：元素从当前位置移动，根据给定的left(x坐标)和top(y坐标)位置参数

* 旋转rotate()：元素顺时针旋转给定的角度。负值：元素将逆时针旋转。

* 缩放scale()：元素的尺寸会增加或减少，根据给定的宽度(X轴)和高度(Y轴)参数。

* 扭曲skew()：元素翻转给定的角度，根据给定的水平线(X轴)和垂直线(Y轴)参数。

* matrix(缩放X轴, , , 缩放Y轴,水平偏移距离, 垂直偏移距离)：使用六个值的矩阵

#### 备注

* 旋转rotate()函数与扭曲skew()函数的区别

rotate()函数只是旋转，而不会改变元素的形状。skew()函数不会旋转，而只会改变元素的形状。

* 缩放(scale)

matrix(sx, 0, 0, sy, 0, 0)->scale(sx, sy)

* 旋转(rotate)

matrix(cos@, sin@, -sin@, cos@, 0, 0)

@表示旋转的角度

* 拉伸(skew)

matrix(1, tan(@y), tan(@x), 1, 0, 0)

@y表示y轴，@x表示x轴

#### Ex

````
div {
    height: 100px;
    width: 100px;
    transform: translate(80px 80px) scale(1.5 1.5) rotate(45deg);
}
//渲染与下面转换一致
<div style="transform: translate(80px 80px)">
    <div style="transform: scale(1.5 1.5)">
        <div style="transform: rotate(45deg)"></div>
    </div>
</div>
````

### 3D转换

#### 语法

````
//3D转换
matrix3d(a1, b2, c3, d4, e5, f6, g7, h8, i9, j10, k11, l12, m13, n14, o15, p16)
translate3d(x, y, z)
translateX(x)
translateY(y)
translateZ(z)
//3D缩放转换
scale3d(x, y, z)
scaleX(x)
scaleY(y)
scaleZ(z)
//3D旋转
rotate3d(x, y, z, angle)
rotateX(angle) //旋转X轴
rotateY(angle) //旋转Y轴
rotateZ(angle) //旋转Z轴
prespective
````

#### 解析

* perspective

透视，视角

决定看到的是2次元还是3次元，即2D transform还是3D transform

CSS3 3D transform的透视点是在浏览器的前方，近似于我们眼睛所在的方位。

* perspective-origin

perspective-origin: x-axis y-axis;

定义3D元素所基于的X轴和Y轴，允许改变3D元素的底部位置。

* backface-visiblity

定义当元素不面向屏幕时是否可见

backface-visiblity: visiblity|hidden;

* translateZ

让元素在自己的眼前或近或远

* transform-style

规定如何在3D空间中呈现被嵌套的元素

transform-style: flat | preserve-3d;

flat: 子元素将不保留其3D位置

preserve-3d: 子元素将保留其3D位置

#### EX

````
//整个作为透视元素
.perspective-global {
    perspective: 600px;
}
//每个元素都有一个自己的视点
.perspective-single {
    transform: perspective(600px) rotateY(45deg);
}
````

### 动画

#### 语法

````
animation: animation-name animation-duration animation-timing-function animation-delay animation-iteration-count animation-direction animation-fill-mode animation-play-state;
````

#### 解析

* animation-name：规定需要绑定到选择器的keyframe名称

* animation-duration：规定完成动画所花费的时间，以秒或毫秒计

* animation-timing-function：规定动画的速度曲线

* animation-delay：规定在动画之前的延迟

* animation-iteration-count：规定动画应该播放的次数

* animation-direction：规定是否应该轮流反向播放动画

* animation-fill-mode: 检索或设置对象动画时间之外的状态

animation-fill-mode: none | forwards | backwards | both;

* animation-play-state: 检索或设置对象动画的状态

#### Ex

````
@keyframe mymove {
    from {left: 0px;}
    to {left: 200px;}
}
div {
    animation: mymove 5s infinite;
}
````

### 参考链接

http://www.zhangxinxu.com/wordpress/2012/06/css3-transform-matrix-%E7%9F%A9%E9%98%B5/comment-page-2/






