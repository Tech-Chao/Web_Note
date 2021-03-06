# 1 盒子模型

## 1.1 看透网页布局的本质：

网页布局的过程：
1. 先准备好相关的网页元素，网页元素基本都是盒子 Box
2. 利用 CSS设置好盒子样式，然后摆放到相应的位置
3. 往盒子里面装内容

网页布局的核心本质：就是利用CSS 摆盒子

# 1.2 盒子模型（Box Model）组成

盒子模型： 就是把 HTML 页面中的布局元素看做是一个矩形盒子，也就是一个盛装内容的容器。

CSS 盒子模型本质是一个盒子，封装周围的 HTML 元素，它包括：边框、外边距、内边距、和实际内容


## 1.3 边框（border）

border: 可以设置边框宽度、边框样式、边框颜色。

```
border: border-width(粗细) ||border-style（样式） || border-color（颜色）
```

border 复合写法对顺序没有要求。边框也可以分四边分别设置：
```
border-top  border-bottom border-left border-right
```
## 1.4 表格细线边框

`border-collapse` 属性控制浏览器绘制表格边框的方式，他控制相邻单元格的边框。

```
<!--  合并相邻的边框。 -->
border-collapse: collapse; 
```

## 1.5 边框会影响盒子实际大小

边框的计入会额外增加盒子的实际代销，因此我们有两种解决方案：

1. 测量盒子大小的时候，不量边框
2. 测量的时候如果包含边框，则需要 width/height 减去边框高度 


## 1.6 内边距（padding）

`padding` 属性用于设置内边距，即边框与内容之间的距离。

···
<!-- 上下左右 -->
padding-top
padding-bottom
padding-left
padding-right
···
可以复合书写，属性可以有1到4个值


  | 值得个数                    | 代表意思                                                           |
  | --------------------------- | ------------------------------------------------------------------ |
  | padding： 5px               | 1个值，代表上下左右都是5px内边距                                   |
  | padding:5px 10x             | 2个值，上下为5px，左右为10px内边距                                 |
  | padding:5px 10px 20px       | 3个值，代表上5px、左右边距 10px 下边距20px                         |
  | padding: 5px 10px 20px 30px | 4个值，上边距5px，右边距10px 下边距20px 左边距30px，顺时针方向设置 |
  
  
  注意；
  - 内容和边框有了距离，添加了内边距
  - padding 会影响盒子实际大小 

如果指定了元素的宽高，新增内边距后会导致元素的实际大小变大。解决方案和外边距一样：让 width/height
 减去多出来的内边距大小即可。

 如果盒子本身没有指定 width/height 属性，则padding 不会撑开盒子大小。


## 1.7  外边距（margin）

margin 属性用于设置外边距，即控制盒子和盒子之间的距离。


  | 属性          | 作用     |
  | ------------- | -------- |
  | margin-left   | 左外边距 |
  | margin-right  | 右外边距 |
  | margin-top    | 上外边距 |
  | margin-bottom | 下外边距 |


margin可以让块级元素居中显示：

- 盒子必须制定宽度
- 盒子左右的外边距都设置 auto
  

  ```
  <!-- 以下三种效果相同 -->
  // 1
  margin-left: auto;
  margin-right: auto;
  // 2
  margin: auto;
  // 3
  margin: 0 auto; （推荐）
  ```

  行内元素及行内块元素水平居中需要给其父元素添加`text-align:ceter`属性即可。

  ## 1.8 外边距合并

  使用 `margin`定义块元素的垂直外边距时，可能会出现外边距的合并。
  
  主要有两种情况：
  
  1. 相邻块元素垂直外边距的合并
  2. 嵌套元素垂直外边距的塌陷

  ### 1.8.1 相邻块元素垂直外边距的合并

  当上下相邻的两个块元素（兄弟关系）相遇时，如果上面的元素有下外边距 `margin-bottom`,下面元素有上边距 `margin-top`,则他们之间的垂直间距不是 `margin-top` 和 `margin-bottom`之和，取两个值中的较大值，这种现象称之为相邻块元素垂直外边距的合并。

 解决方案：设置一个外边距。

  ### 1.8.2  嵌套元素垂直外边距的塌陷
  
  对于两个嵌套关系（父子关系）的块元素，父元素有上外边距同事子元素也有上外边距，此时父元素会塌陷较大的外边距值。 

解决方案:
- 可以为父元素定义上边框
- 可以为父元素定义上内边距
- 可以为父元素添加 `overflow: hidden`属性

## 1.9 清除内外边距

网页元素很多都带有默认的内外边距，而且不同浏览器默认的也不一致，因此我们在布局时，首先要清除下网页元素的内外边距:

```
* {
    padding: 0;
    margin: 0;
}
```

注意： 行内元素为了照顾兼容性，尽量值设置左右内外边距，不要设置上下内外边距，但是转换为块级和行内块元素就可以了。


## 1.10 圆角边框（重点）

在 CSS3 中，新增圆角边框样式，这样我们的盒子就可以变圆角了。

语法：

```
border-radius: length;
```
radius 圆角原理： （椭）圆与边框的交集行程圆角效果

- length 可以是像素值，也可是百分比。
- length 可以有1、2、3、4个值，按顺时针的方向，每个角设置不同的弧度。
- 可以分别设置：`border-top-left-radius、border-top-right-radius、border-bottom-right-radius、border-bottom-left-radius、`


## 1.11 盒子阴影

在 CSS3中新增盒子阴影，我们可以使用`box-shadow`属性为盒子添加阴影。

语法：
```
 box-shadow:h-shadow v-shadow blur spread color inset;
```

  | 值       | 秒速                                   |
  | -------- | -------------------------------------- |
  | h-shadow | 必填，水平阴影的位置，允许负值         |
  | v-shadow | 必填，垂直阴影的位置，允许负值         |
  | blur     | 可选，模糊距离                         |
  | spread   | 可选，阴影的尺寸                       |
  | color    | 可选，阴影的颜色，参阅CSS 颜色值       |
  | inset    | 可选，将外部阴影（outset）改为内部阴影 |

  注意：
  - 默认的是外阴影（outset），但不可以写这个单词，写这个单词会导致外阴影无效
  - 盒子阴影不占用空间，不会影响其他盒子排列。


## 1.12 文字阴影

在 CSS3中新增文字阴影，我们可以使用`text-shadow`属性为文字添加阴影。

语法：

```
text-shadwo: h-shadow v-shadow blur color
```


  | 值       | 秒速                             |
  | -------- | -------------------------------- |
  | h-shadow | 必填，水平阴影的位置，允许负值   |
  | v-shadow | 必填，垂直阴影的位置，允许负值   |
  | blur     | 可选，模糊距离                   |
  | color    | 可选，阴影的颜色，参阅CSS 颜色值 |