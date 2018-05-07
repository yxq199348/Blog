### transition 过渡

**语法**
````
transition: transition-property transition-duration transition-timing-function transition-deplay
````

**备注**
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



