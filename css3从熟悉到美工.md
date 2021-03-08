# css3从熟悉到美工

## 如何学习

1.CSS是什么

2.css怎么用(快速入门)

3.css选择器(重点和难点)

4.美化网页(文字,阴影,超链接,列表,渐变...)

5.盒子模型

6.浮动

7.定位

8.网页动画

## 2 选择器

### 三种基本的选择器

标签选择器，id选择器，class选择器

优先级：id选择器>class选择器>标签选择器

class选择器=> .XXX:

id选择器=> #XXX:

标签选择器=> XXX:

### 层次选择器

1.后代选择器：在某个元素的后面 祖爷爷 爷爷 爸爸 你

```css
/*后代选择器*/
body p{
	background: red;
}
```

2.子选择器：一代，儿子

```css
/*子选择器*/
body>p{
    background: #3cbda6;
}
```

3.**相邻(向下)**兄弟选择器  同辈

```CSS
/*兄弟选择器*/
.active + p{
    background: #a13d30;
}
```

4.通用选择器(当前选中元素的***向下的***所有兄弟元素):

```CSS
.active~p{
    background: #02ff00;
}
```

### 结构伪类选择器

伪类：条件

```css
/*ul的第一个子元素*/
ul li:first-child{
    background: #02ff00;
}

/*ul的最后一个元素*/
ul li:last-child{
    background: #02ff00;
}

/*选中p1:定位到父元素，选择当前第一个元素
选择当前p元素的父级元素，选中父级元素的第一个，并且是当前元素才生效！*/
p:nth-child(2){
    background: #2700ff;
}

/*选中父元素下的p元素的第二个类型*/
p:nth-of-type(1){
    background: yellow;
}
```

### 属性选择器(常用)

```css
/*存在id属性的元素 a[]{} */
a[id]{
     	background: #63ff23;
     }
/*存在class属性包含item的元素*/
a[class*="item"]{
        background: black;
	}
```

## 3 美化网页元素

### 为什么要美化网页

1.传递的传递网页信息

2.美化网页，页面飘来你给，才能吸引用户

3.凸显页面的主题

4.提交用户的体验

### 常用标签

#### span标签：重点要突出的字,使用span套起来

#### font标签：定义字体样式如下

```css
font-family: "Arial Black", 楷体;
color: red;
font-size: 50px;
font-weight: bolder;
```

#### 文本样式

```css
/*
rgba() 函数使用红(R)、绿(G)、蓝(B)、透明度(A)的叠加来生成各式各样的颜色。
R,G,B:0-255间的整数，分别代表颜色中的红绿蓝
A:透明度，取值0-1之间，代表透明度
*/
color: rgba(0,255,255,0.9);
text-align: left;
/*text-indent:2em; 段落首行缩进*/
text-indent: 2em;
/*行高和块的高度一致即可上下居中(例如这里的height和line-height都为300像素)*/
height: 300px;
line-height: 300px;   //行高
/*文本图片水平对齐*/
vertical-align:middle
/*装饰*/
text-decoration:
```

#### 文本阴影和超链接伪类

```css
/*未访问的链接*/
a:link {color:red;}
/*已访问的链接*/
a:visited {color:red;}
/*鼠标悬停的链接*/
a:hover {color:red;}
/*已选择的链接*/
a:active {color:red;}

/*
文本阴影 
h-shadow:必需。水平阴影的位置。允许负值。
v-shadow:必需。垂直阴影的位置。允许负值。
blur:可选。模糊的距离。
color:可选。阴影的颜色。参阅 CSS 颜色值。
*/
text-shadow: h-shadow v-shadow blur color;
/*例如:text-shadow: 5px 5px 5px #FF0000;*/
```

#### 列表

我们创建的无序列表往往在前面会有一个小圆点，可以利用css去掉

```css
/*
list-style:
   none;  去掉原点
   circle  空心圆
   decimal 数字
   square  正方形
*/
list-style: none;
```

#### 背景

```css
div
  {
  /*第一个是边框的宽度，第二个是边框的样式(这里为实线),第三个是边框的颜色 */
  border:5px solid red; 
  }
```

```css
/*背景图片的平铺效果，平铺即为图片的重复，若一个小图片加到一个大的div，会默认重复很多个然后填充满div */
.div1
	{
    background-repeat: repeat-x;  /*水平平铺*/
    background-repeat: repeat-y;  /*垂直平铺*/
    background-repeat: no-repeat;  /*不平铺*/
    }
```

```css
/*背景图片的填充*/
/*属性依次是：颜色，图片地址，图片位置，平铺方式*/
background: red url("../images/d.gif") 270px 10px no-repeat
```

```css
/*渐变色(了解)*/
background-image: linear-gradient(115deg,#FFFFFF 0%, #6284FF 50%, #FF0000 100%)
```

#### 盒子模型

什么是盒子

![CSS box-model](https://www.runoob.com/images/box-model.gif)

```css
margin:外边距
padding:内边距
border:边框
```

##### 边框

1.边框的粗细

2.边框的样式

3.边框的颜色

```css
/*边框粗细，边框风格，边框颜色*/
border:5px solid red
```

##### 外边距

```css
/*依次为上下左右设置外边距*/
padding: 0 0 0 0;
/*padding两个属性是分别为上下和左右*/
padding:0 0;
/*外边距的妙用：居中元素*/
margin: 0 auto;
/*分别设置外边距上下左右*/
margin-top: 0;
margin-bottom: 0;
margin-left: 0;
margin-right:0;
```

##### 内边距

```css
/*语法与外边距差别不大*/
padding: 0 0 0 0;
```

##### 内外边距的区别

1.margin和padding都是盒模型(Box Model)的重要元素，二者都是用来处理与其他盒子的距离关系进行布局的。

2.形象的介绍，夏季女生在地铁遇到色狼变态时有发生，如果选择穿上羽绒服与色狼保持距离，那就是padding内边距，如果选择移动自己的位置远离色狼，那就是margin外边距。

3.就与borde边框的位置来看，pading在border边框内，margin在border边框外。

4.padding内边距会改变盒模型的大小（即宽高），margin则不会。

5、margin内边距用负值，pading不可以。

## 常用的css语言

```css
/*鼠标停在超链接背景会变成红色，移开又还原*/
a:horver{
    red;
}
```

