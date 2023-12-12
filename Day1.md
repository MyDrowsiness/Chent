# 一、平面转换transform

## 1.概念

#### 作用

为元素添加动态效果，一般与过度配合使用。

#### 概念

改变盒子在平面内的形态（位移、旋转、缩放、倾斜）。

#### 代码

```html
<style>
    div{
        margin: 100px 0;
        width: 100px;
        height: 100px;
        background-color: pink;;
        transition: all 1s;
    }
    /* 鼠标滑过：添加动态效果 */
    div:hover{
        transform: translate(800px) rotate(360deg) scale(2) skew(30deg);
    }
</style>
```

transform平面转换，一般搭配transition使用：
平移：translate(800px)
旋转：rotate(360deg)
缩放：scale(2)
倾斜：skew(30deg)

#### 拓展

平面转换又叫 2D转换。

## 2.平面转换-平移

#### 属性

transform:translate(X轴移动距离，Y轴移动距离)；

#### 取值

像素单位数值。
百分比(参照盒子自身尺寸计算结果)。
正负均可。

#### 技巧

translate()只写一个值，表示沿着X轴移动。
单独设置X或Y轴移动距离：translateX()或translateY()。

#### 代码

```html
<style>
    .father{
        width: 500px;
        height: 300px;
        margin: 100px auto;
        border: 1px solid #000;
    }
    .son{
        width: 200px;
        height: 100px;
        background-color: pink;
        transition: all 0.5s;
    }
    /* 鼠标移入到父盒子，son改变位置 */
    .father:hover .son{
        /*像素*/
        transform: translate(300px,200px);
        /*百分比：参照盒子自身尺寸计算结果*/
        transform: translate(-50%,100%);
    }
</style>
<div class="father">
    <div class="son"></div>
</div>
```

#### 拓展

绝对定位元素居中（例如：登录框）

```html
<style>
    .box{
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%,-50%);
        width: 200px;
        height: 100px;
        background-color: pink;
    }
</style>
```



## 3.平面转换-旋转

#### 属性

transform:rotate(旋转角度deg)
角度单位是deg

#### 技巧

取正负均可
取值为正，顺时针旋转
取值为负，逆时针旋转

#### 代码

```html
<style>
    img{
        margin: 200px 600px;
        width: 200px;
        transition: all 2s;
    }
    /* 鼠标悬停到图片上面，添加旋转效果 */
    img:hover{
        /* 正数：顺时针旋转；负数：逆时针旋转 */
        transform: rotate(720deg);
        transform: rotate(-720deg);
    }
</style>
```

## 4.平面转换-改变转换原点

默认情况下，转换原点是盒子中心点

#### 属性

transform-origin:水平原点位置 垂直原点位置

#### 取值

✿方位名词(left、top、right、botten、center)
像素单位数值
百分比

## 5.平面转换-多重转换

#### 技巧

transform: translate() rotate();

#### 代码

```html
<style>
    .box{
        margin: 200px 350px;
        width: 800px;
        height: 200px;
        border: 1px solid #000;
    }
    img{
        width: 200px;
        transition: all 5s;
    }
    /* 鼠标移入box,图片边走边转 */
    .box:hover img{
        /* 先平移再旋转（目标效果） */
        transform: translate(600px) rotate(360deg);
        /* 
        先旋转再平移
        旋转会改变坐标轴向，导致效果不一样  
        多重转换：一第一种转换形态的坐标轴为准 
        */
        transform: rotate(360deg) translate(600px);
        /* 层叠性，会被后面属性覆盖 */
        transform: translate(600px);
        transform: rotate(360deg);
    }
</style>
```

## 6.平面转换-缩放

#### 思考

改变元素的width或height属性能实现吗？
注：该方法从左上角开始放大。

#### 属性

transform: scale(缩放倍数)；
transform: scale(X轴缩放倍数，Y轴缩放倍数);

#### 技巧

通常，只为scale()设置一个值，表示X轴和Y轴等比例缩放
取值大于1表示放大，取值小于1表示缩小

## 7.平面转换-倾斜

#### 属性

transform: skew();

#### 取值

角度度数deg





# 二、渐变

## 1.概念

#### 定义

渐变是多个颜色逐渐变化的效果，一般用于设置盒子背景

#### 分类

1.线性渐变
2.径向渐变

## 2.线性渐变

#### 属性

```html
background-image: linear-gradient(
	渐变方向,
	颜色1 终点位置,
	颜色2 终点位置,
	……
);
```

#### 取值

渐变方向：可选
	to 方位名称
	角度度数
终点位置：可选
	百分比

## 3.径向渐变

#### 作用

给按钮添加高光效果

#### 属性

```
background-image: radial-grandient(
	半径 at 圆心位置,
	颜色1 终点位置,
	颜色2 终点位置,
	……
);
```

#### 取值

半径可以是2条，则为椭圆
圆心位置取值：像素单位数值/百分比/方位名词