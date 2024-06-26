# CSS 的三个特性

在了解CSS之前，我们先来了解一下CSS的三个特性。这对后续学习尤为重要。

!> 本章节所讲述的概念很抽象，但这些抽象的概念同样能指导后续的学习，所以也必须先从这些概念学起。

## 继承性

继承，指的是特定的 CSS 属性可以从父元素向下传递到子元素。

其特性就是：子元素有默认继承父元素样式的特点。  
作用：恰当的使用继承可以简化代码，降低 CSS 样式的复杂性。

可以继承的常见属性：`color`、`font-style`、`font-weight`、`font-size`、`font-family`、`text`系列、`line`系列等。

总的来说就是控制文字的都能继承，而其他不能继承（包括但不限于盒子、定位、布局）。

**继承失效的情况：**
- a标签本身具有color颜色属性，继承失效
- 标题h系列本身具有font-size字体大小属性，继承失效

让我们来看个案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>鲶大禹的学习笔记</title>
    <style>
        /* 继承性 */
        div {
            /* 控制文字的都能继承，其他不能继承 */
            color: red;
            font-size: 20px;
            height: 100px;
        }
    </style>
</head>
<body>
    <div>
        div
        <span>span</span>
        <a href="#">超链接</a>
        <h1>h1</h1>
    </div>
</body>
</html>
```

在浏览器中呈现的效果：

![继承性](https://s21.ax1x.com/2024/04/05/pFbfn8P.png)

我们发现，我并没有给 `span` 和 `h1` 标签设置红色字体的属性，但是它们继承了父元素 `div` 的属性，因此字体也会跟着变成红色。

上图中 `a` 标签不能继承红色，`h1` 标签不能继承字体大小。

## 层叠性

CSS全名叫Cascading Style Sheet（层叠样式表），名字就说明了它所具有的属性——层叠性。

也就是说，一个 HTML 文档可能会使用多种 CSS 样式单，细化到某元素来说，会层叠多层样式单，但生效的总会有一个顺序，即样式生效的优先级如下：

```
内联样式 --> 内部样式 --> 外部样式 --> 浏览器默认效果
```

特性：

- 给同一个标签设置不同的属性，样式会层叠**叠加**，共同作用在标签上
- 给同一个标签设置相同的属性，样式会层叠**覆盖**，最终写在最后的样式才会生效

!> **注意：**当样式冲突时，只有当选择器优先级相同，才能通过层叠性判断结果。*（优先级的概念将在下个小节中讲述）*

例如：

```css
    div{
        color: red;
        color: blue;
    }
```

根据**给同一个标签设置相同的属性，样式会层叠覆盖，最终写在最后的样式才会生效**的规则。  
此时div中的文字会显示**蓝色**而不是两者都有。

## 优先级

在 CSS 中，不同的选择器会拥有不同的优先级，而优先级高的选择器则会覆盖优先级低的选择器。

事实上，当某元素层叠到的样式表较多时，我们就会对样式单进行权重排序，即优先级。

优先级公式如下：

```
通配符选择器 < 标签选择器 < 类选择器 < id选择器 < 行内样式 < !important
```
?> 我们发现，当选中的范围越大时，优先级越低

!> 请注意，!important 是提权功能，提高权重/优先级别到 **最高** ，但是慎用。因为在开发中，我们并不能保证某个样式权重永远是最高的。

在使用 `!important` 时，我们需要注意：

1. !important 写在属性值后面，封号的前面。
2. !important 不能提升继承的优先级，**只要是继承，优先级必然最低**。
3. 在实际开发中，并不推荐使用!important。

### 优先级 - 叠加计算规则

当某元素层叠到的样式单较多时，我们通常会对样式单进行权重排序，计算方式如下：

?> **公式：**行内样式 - id选择器个数 - 类选择器个数 - 标签选择器个数

![公式](https://s21.ax1x.com/2024/04/05/pFbWy1f.png)

现在，让我们来了解一下它的规则：
- 根据公式 **从左向右** 依次比较选个数，**同一级** 个数多的优先级高，如果个数相同，则向后比较。
- !important 权重最高
- 继承权重最低

了解完规则和公式，让我们看一个实例：

CSS代码：
```css
.c1 .c2 div { 
    color: blue;
}

div #box3 {
    color:green;
}

#box1 .c3 {
    color:orange;
}
```

HTML代码：
```html
<div id="box1" class="c1">
  <div id="box2" class="c2">
    <div id="box3" class="c3">
      这行文本是什么颜色的？
    </div>
  </div>
</div>
```

那么，这行文本会显示什么颜色呢？

根据刚刚所学习的公式和规则，我们得出以下结论：

```css
/* (0, 0, 2, 1) */
.c1 .c2 div { 
    color: blue;
}

/* (0, 1, 0, 1) */
div #box3 {
    color:green;
}

/* (0, 1, 1, 0) */
#box1 .c3 {
    color:orange;
}
```

首先，我们先判断是否有特殊情况，即有 **!important** 权重 或 有 **继承**。  
在上述案例中，均没有最高权重和继承元素。那么我们就需要根据公式来依次判断。

第一个样式，我们判断其<font style="color: #42b983;font-weight: bold">没有行内样式</font>，所以第一个为<font style="color: #42b983;font-weight: bold"> 0</font>。  
我们又判断其<font style="color: #42b983;font-weight: bold">没有id选择器</font>，所以第二个也为<font style="color: #42b983;font-weight: bold"> 0</font>。  
但是我们发现，第一个样式中存在.c1 .c2<font style="color: #42b983;font-weight: bold">两个类选择器</font>，所以第三个为<font style="color: #42b983;font-weight: bold"> 2</font>。  
最后判断是否有标签选择器，在此案例中，<font style="color: #42b983;font-weight: bold">有标签选择器div</font>，因此最后一个为<font style="color: #42b983;font-weight: bold"> 1</font>。

故第一个样式给出的权重就为（0, 0, 2, 1）

用同样的判断方式判断接下来的样式，我们就可以得出三个权重为：  
1. **(0, 0, 2, 1)**
2. **(0, 1, 0, 1)**
3. **(0, 1, 1, 0)**

接下来，我们根据规则来进行比较：

第一位数都为 0 ，所以继续向后比较。  
第二位数只有一个样样式为 0 ，所以第一个样式就被排除了（即不生效）。  
第三位数我们发现，第三个样式为 1 ，而第二个样式为 0 ，所以最后结论为第三个样式生效。  