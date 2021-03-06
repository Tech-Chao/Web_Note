# CSS笔记——CSS3进阶

## CSS3 2D 转换

转换（transform）是 CSS3 中具有颠覆性的特征之一，可以实现元素的位移、旋转、缩放等效果。

转换（transform）可以简单的理解为变形：
- 移动：translate
- 旋转： rorate
- 缩放： scale

## 2D转换 之移动 translate

2D移动时2D转换里面的一种功能，可以改变元素在页面的位置，类似定位。

语法：

```
transform:translate(x,y); 
// 或者分开写：
transform:translateX(n); 
transform:translateY(n); 

```

重点：
- 定义 2D 转换中的移动，沿着 X 和 Y 轴移动元素
- translate 最大的有点：不会影响到其它元素
- translate 中的百分比单位是相对于自身元素宽高如:translate:(50%,50%)
- 对行内标签没有效果

## 2D 转换之 旋转 rorate

2D旋转指的是让元素在二维平面内顺时针旋转或者逆时针旋转。


语法：

```
transform:rorate(度数);
```

重点：

- rorate 里面的读书，单位是 deg，如 rorate(45deg)
- 正值为顺时针，负值逆时针旋转
- 默认选择中心点时元素的中心点

## 修改 2d 转换的中心点

元素转换的中心点我们可以通过css来设置

语法
```
transform-origin: x y;
```

重点：
- 注意x y 以空格分开
- x y 默认转换的中心点是元素的中心点（50% 50%）
- 还可以给 x y 设置像素或者 方位名词（top bottom left right center）

## 2D 转化之缩放scale

缩放，顾名思义，可以对元素进行放大缩小，只要给元素添加了这个属性就能控制它的放大或者缩小

语法：
```
transform:scale(x,y);
```
注意：
- x，y 以逗号分隔
- transform:scale(1,1) 宽高缩放1倍，相当于没有放大缩小
- transform:scale(2,2) 宽高放大了2倍
- transform:scale(2),只写一个参数时相当于x，y都是2（transform：scale(2,2)），宽高放大2倍。
- transform:scale(0.5,0.5) ,元素宽高缩小到原来的一半
- scale 的最大优势：可以设置转换的中心点缩放（默认以中心点缩放），而不影响其它盒子。     

## 2D转换 综合写法

注意：

- 可以同时使用多个转换，格式为`transform:translate() rorate() scale()`
- 其顺序会影响转换结果
- 当我们同时有位移和其它属性时，记得将位移前置
  


 ## 2D转换总结

- 转换transform 我们简单理解就是变形，变形还有2D 和 3D 之分
- 我们目前学了 位移、 旋转 和 缩放
- 2D移动 translate（x,y）最大的优势在于不会影响其他盒子，里面参数如果是%,则会相对自身的宽高来计算
- 可以分开写translateX(n)和translateY(n)
- 2D旋转rorate（度数），可以实现元素旋转，度数的单位是 deg
- 2D缩放scale（x,y）里面的参数是数字，不带单位，可以是小数，最大的优势也是不会影响其他盒子
- 设置转换中心点 transform-origin:x y; 参数可以是百分比 像素 或者是 方位名词
- 当我们进行综合写法时，记得位移属性前置。
 
# CSS3 动画

##  动画的基本使用

动画（animation）是CSS3中具有颠覆性的特征之一，可以通过设置多个节点来精确控制一个或一组动画，来实现复杂的动画效果，相较与过渡，动画可以实现等多变化、更多控制、连续自动播放效果。

制作动画步骤：
1. 先定义动画
2. 在调用动画

### keyframes 定义动画

语法:

```
@keyframes 动画名称 {
    0% {
        width:100px;
    }

    100% {
        width 200px;
    }
}
```

### 元素使用动画

语法：

```
div {
    width:200px;
    ...

    animation-name:动画名称;
    animation-duration:持续时间;
}
```

### 动画序列

- 0%是动画开始状态，100%是动画结束状态，这样的规则就是动画序列
- 在 @keyframe 中规定某项 CSS 样式，就能创建由当前样式逐渐变为信阳市的动画效果
- 动画就是使元素从一种样式逐渐变化为另一种样式的效果，可以改变**任意多的样式任意多的次数**
- 用百分比来规定变化发生的时间，或者用关键字 from 和 to。等同于 0% 和 100%

## 动画的属性

参考 MDN 上属性表

## 动画简写
语法：
```
animation: 动画名称 持续时间 运动曲线 何时开始 播放次数 是否反向 动画起始或者结束的状态;
```

## 3D 转换 

3D 特点：

- 近大远小
- 物体后面遮挡不可见
  
当我们在网页上构建3D效果的时候可以参考这些特点就能产出3D效果

### 三维坐标

三维坐标相对二维坐标来说多了一个 z 轴

- x轴：水平向右 注意：x 右边是正值，左边是负值
- y轴：垂直向下 注意： y下面是正值，下面是负值
- z 轴 垂直屏幕 注意：往外面试正值，往里面是负值

### 3D位移

3D移动相对 2D位移的基础上多了一个可以移动的方向就是 z 轴


- transform:translateX(n); 仅在 x 轴 移动
- transform:translateY(n); 仅在 y 轴 移动
- transform:translateZ(n); 仅在 z 轴 移动（一般使用 px 单位）
- transform:translate3d(x,y,z); 分别在 x y z 轴上移动


### 透视 perspective

在 2D 平面产生近大远小视觉立体，但是只是效果二维的

- 如果想要在网页产生 3d 效果需要透视（理解为 3d 物体投影在2d平面内）
- 模拟人类的视觉位置，可认为安排一只眼睛去看
- 透视我们也称为视距；视距就是人的眼镜到屏幕的距离
- 距离视觉点越近的在电脑平面成像越大，越远成像越小
- 透视的单位是像素

注意透视需要写在被观察元素的父盒子上：

d: 就是视距，视距就是眼睛距离屏幕的距离
z: 就是 z 轴，物体距离屏幕的距离，z 轴越大（正值）我们看到的物体就越大

以上两个属性都会影响3d的效果。

### translateZ

`transform: translateZ(100px)`:仅仅是在 Z 轴上移动，有了透视就能看到 transformZ的效果了（近大远小）


### 3D旋转

3D 旋转是指元素可以在三维平面上沿着 X 、Y、Z轴或者自定义轴上旋转。
语法：
```
transform:rorateX(45deg);沿着X轴正方向旋转45度
transform:rorateY(45deg);沿着Y轴正方向旋转45度
transform:rorateZ(45deg);沿着Z轴正方向旋转45度
transform:rorate3d(x,y,z);沿着自定义轴方向旋转 自定义 角度
```

旋转的方向,记住左手准则：大拇指指向 x 轴的正方向，其余手指弯曲的方向就是元素沿着x轴旋转的方向。(y 、z 轴一样判断)


### 3D呈现 transform-style

- 控制子元素是否开启三维立体环境
- transform-style:flat 子元素不开启3d立体空间
- transform-style：preserve-3的；子元素开启立体空间
- 代码写给父级，但是影响的是子盒子
- 这个属性很重要，后面比用