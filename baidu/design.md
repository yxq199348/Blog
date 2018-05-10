### transition 过渡

**语法**
````
transition: transition-property transition-duration transition-timing-function transition-deplay
````

**解析**
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

**Ex**
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

**语法**
````
transform: translate(x, y) / rotate(n deg) / scale(x, y) / skew(x, y) / matrix(a, b, c, d, e, f)
transform-origin：x-axis y-axis z-axis
````

**解析**
* 位移translate(n deg)：元素从当前位置移动，根据给定的left(x坐标)和top(y坐标)位置参数

* 旋转rotate()：元素顺时针旋转给定的角度。负值：元素将逆时针旋转。

* 缩放scale()：元素的尺寸会增加或减少，根据给定的宽度(X轴)和高度(Y轴)参数。

* 扭曲skew()：元素翻转给定的角度，根据给定的水平线(X轴)和垂直线(Y轴)参数。

* matrix()：使用六个值的矩阵

**备注**
* 旋转rotate()函数与扭曲skew()函数的区别

rotate()函数只是旋转，而不会改变元素的形状。skew()函数不会旋转，而只会改变元素的形状。

**Ex**
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






