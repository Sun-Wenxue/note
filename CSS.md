# CSS

## 1 简介

cascading style sheets层叠样式表

为结构化文档添加样式

文件后缀.css

## 2 语法

```css
h1 /*选择器*/
{
	color:blue;	/*由属性:值;组成的声明*/
}
```

## 3 选择器

### id选择器

#id名，不要以数字开头

### class选择器

.class名

## 4 样式表

### 外部样式表

应用于很多页面的样式，在头部使用link

```
<head>
<link rel=“stylesheet” type="text/css" href="mystyle.css">
</head>
```

.css文件由各种选择器及其声明组成

### 内部样式表

单个文档的特殊样式，直接用style标签

```
<head>
<style>
hr {xx:xx;}
p {xx:xx;}
body {xx:xx;}
</style>
</head>
```

### 内联样式

样式仅需要在一个元素上应用一次

```
<p style="xx:xx;">xxx</p>
```

多重样式优先级：由内而外

## 5 背景

颜色，图像，平铺，位置等

颜色：十六进制/RGB/颜色名称

## 6 文本

文本颜色，对齐方式，修饰（线），（大小写）转换，首行缩进

## 7 字体

字型，（备选）字体系列，字体样式（斜体），大小

## 8 链接

a:link/visited/hover/active 未访问/已访问/悬停/点击链接可以分别设置样式

## 9 列表

列表标记的类型，图像属性等

如可以用ul.a{}来指定无序列表class="a"的样式

## 10 表格

表格边框，边框折叠，宽高，文字对齐，单元格的填充，表格颜色

## 11 盒子模型

<img src="https://www.runoob.com/images/box-model.gif" alt="CSS box-model" style="zoom:50%;" />

和模型可以封装HTML元素，定义外边距，边框，内边框和内容的样式

设置HTML中div的样式来设置盒模型

## 12 边框

边框的样式，宽度，颜色，可以单独设置各条边的样式

## 13 轮廓

在元素周围划线

## 14 外边距

<img src="https://www.runoob.com/wp-content/uploads/2013/08/VlwVi.png" alt="img" style="zoom:50%;" />

清除边框周围的区域

## 15 填充

用内容的背景颜色填充

## 16 分组和嵌套选择器

### 分组选择器

不同选择器相同样式可以合并，选择器逗号隔开 

### 嵌套选择器

可以为有不同嵌套关系的元素设置样式

## 17 尺寸

控制高度宽度，设置最大最小限制

## 18 显示与可见性

隐藏（占用/不占用空间）

块和内联（占据一行/不必另起一行）

## 19 定位

static：静态定位，文档流中的正常位置，不受top/bottom/left/right影响

fixed：固定位置

relative: 相对正常位置移动

absolute: 通过最近的父元素定位，不占文档流空间可能与其他元素重叠

stiky: 依赖用户滚动定位

z-index: 重叠元素可以设置堆叠顺序

## 20 overflow

内容溢出时，修剪或通过滚动条展示

## 21 float

在水平方向上尽量浮动直到碰到边界，周围元素重新排列

## 22 对齐

水平/垂直居中对齐

## 23 组合选择符

" "后代选择器，任何满足条件的后代都适用

">"子元素选择器，只有直接的父子关系适用

"+"相邻兄弟选择器，紧邻的兄弟关系适用

"~"后续兄弟选择器，所有后续的兄弟关系都适用

## 24 伪类

类：xx.class class要在元素里说明才有效

伪类：xx:pseudoclass 伪类时预定义的关键字

anchor伪类：link/visited/hover/active

:first-child父类的（可以是第一个）子元素

:lang特殊元素的对应语言

## 25 伪元素

特殊的选择器，为选择器对应的元素添加特殊效果

为首行或首字母设置样式，在标题前插入图片等

## 26 导航栏

基于无序列表\<ul\>，列表的每一行都是链接

\<ul\>的样式：删除默认的圆点，边距，填充

链接\<a\>的样式：整体可点的块

:hover悬停时有特殊样式

.active激活后的特殊样式

调整居中，高度，内联，浮动，分割线等

## 27 下拉菜单

CSS:

.dropdownbtn设置按钮样式

.dropdown设置菜单

.dropdown-content 设置内容样式

hover设置悬停时显示

html：

div class="dropdown"封装整个菜单

​	button class="dropbtn"指定悬停显示菜单的按钮

​	div class-"dropdown-content"设置下拉菜单的内容

## 28 弹性盒子(flex-box)

弹性容器(Flex container)

弹性元素(Flex item)

弹性元素能够在弹性盒子中灵活布局，如排列和对齐

## 29 flex布局

### 基本概念

<img src="https://picx.zhimg.com/v2-54a0fc96ef4f455aefb8ee4bc133291b_1440w.jpg" alt="img" style="zoom: 80%;" />

默认两条轴：水平主轴(main axis)，垂直交叉轴(cross axis)

### flex item

每个单元块占据的主轴空间(main size)，交叉轴空间(cross size)

属性

| 属性      | 说明           | 属性        | 说明               |
| --------- | -------------- | ----------- | ------------------ |
| order     | 容器的排列顺序 | flex-basis  | 主轴空间，可auto   |
| flex-grow | 自适应放大比例 | flex-shrink | 自适应缩小比例     |
| flex      | flex-xxx的组合 | align-self  | 单个项目的对齐方式 |

flex container：生成容器盒子

