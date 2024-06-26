<style>
    .zoomImage {
        width: 23%;
    }
    .zoomImage70 {
        width: 70%;
    }
    @media only screen and (max-width: 768px) {
        .zoomImage {
            width: 67%;
        }
        .zoomImage70 {
            width: 100%;
        }
    }
</style>

# CSS的选择器

作用：**查找标签**，设置样式。 

在 CSS 中，我们必须规范地选中某个标签或者元素，才能对其设置样式。

?> 由于 CSS 选择器的多样性，我不得不将其单独作为一个章节来讲解。

## 标签选择器

标签选择器：使用**标签名**作为选择器 → 选中**同名标签设置相同的样式**。

标签选择器又称元素选择器，是最简单的选择器，选择器通常是某个HTML元素，甚至可以是HTML本身。  
其写作格式如下：

```css
标签名 {
  属性名: 属性值;
}
```

例如：p, h1, div, a, img......

```html
<style>
  p {
    color: red;
  }
</style>

```

值得注意的是，标签选择器**无法差异化**同名标签的显示效果。  
也就是说，当你写了一个 p 标签的样式为红色，那么所有 p 标签都会变成红色。  
如果需要解决这个问题，那么就需要引入接下来的内容。

## 类选择器

作用：查找标签，**差异化**设置标签的显示效果。

在 CSS 中，类选择器以一个点 `.` 号来定义  
类选择器可以为指定 class 的 HTML 元素指定样式。  
其写作格式如下：

```css
.类名 {
  属性名: 属性值;
}
```

步骤：

* 定义类选择器 → **.类名**
* 使用类选择器 → 标签添加 **class="类名"**

```html
<style>
  /* 定义类选择器 */
  .red {
    color: red;
  }
</style>

<!-- 使用类选择器 -->
<div class="red">这是 div 标签</div>
<div class="red size">div 标签</div>
```

注意：

* 类名**自定义**，但不可以用纯数字或中文，尽量用英文命名
* 一个类选择器**可以供多个标签使用**
* **一个标签可以使用多个类名**，类名之间用**空格**隔开

针对第三点，我们来看一个案例：

```html
<div class="class1 class2">这个盒子将被应用两个类样式</div>
```

这就是 `一个标签可以使用多个类名，类名之间用空格隔开` 的含义

?> **开发习惯：**类名见名知意，多个单词可以用 `-` 连接，例如：`news-hd`

## id选择器

作用：查找标签，**差异化**设置标签的显示效果。

场景：id 选择器一般**配合 JavaScript** 使用，很少用来设置 CSS 样式

CSS 中 id 选择器以 "#" 来定义  
严格来讲，在一份 HTML 文档中，id值都是<font style="color:#42b983;font-weight: bold;">唯一的</font>，因为如果出现了两个相同的id值，JavaScript 只会取第一个具有该id值的元素。


其写作格式如下：

```css
#id名 {
  属性名: 属性值;
}
```

步骤：

* 定义 id 选择器 → #id名
* 使用 id 选择器 → 标签添加 id= "id名"

```html
<style>
  /* 定义 id 选择器 */
  #red {
    color: red;
  }
</style>

<!-- 使用 id 选择器 -->
<div id="red">这是 div 标签</div>
```

同样的，id名可以自定义，且不可以数字开头，不能出现空格，因为这在 JavaScript 中不是一个合法的变量名。  
name、class 等属性值的书写规范与id值是一样的，不同的是它们不具备唯一性。

## 通配符选择器

作用：查找页面**所有**标签，设置相同样式。

通配符选择器（Universal Selector）也是一种简单选择器，用 `*` 表示，一般称之为通配符，表示对任意元素都有效。  
 **不需要调用**，浏览器自动查找页面所有标签，设置相同的样式。

 其写作格式如下：

 ```css
* {
  属性名: 属性值;
}
 ```

> 通配符选择器可以用于**清除标签的默认样式**，例如：标签默认的外边距、内边距。

例如：

```css
* {
  margin: 0;
  padding: 0;
}
```

## 派生选择器/上下文选择器

派生选择器依据元素在其位置的上下文关系定义样式，我们又称它文档结构选择器或父子选择器。但无论你如何称呼它们，它们的作用都是相同的。  
派生选择器大致可以分为4种：**后代选择器、子元素选择器、相邻兄弟选择器、通用兄弟选择器**。

在正常的开发中，我们要写的标签会非常之多。可能会存在像如下代码这种**标签中嵌套标签的情况：**

```html
<body>
  <p>我是第一层第一个</p>
  <p>我是第一层第二个</p>
  <p>我是第一层第三个</p>
  <ul>
    <p>我是第二层第一个</p>
    <p>我是第二层第二个</p>
    <li>
      <p>我是第三层第一个</p>
      <p>我是第三层第二个</p>
      <p>我是第三层第三个</p>
    </li>
  </ul>
</body>
```

如果我们只想选择第三层的全部p标签，该如何写选择器呢？

当然了，我们使用 id和 class的方式能够很快的完成这一操作。**除此之外，我们还有更便捷的方法。**

### 后代选择器

后代选择器这个概念很好理解，相信在学习HTML的时候，我们已经对父子级有了基本的了解，那我们代入辈分就好了。

- 在最外面的 `<body>` 我们将其理解为曾祖父
- 再往里就是第一层的 `<p>` 标签和 `<ul>` 标签了，我们将其理解为祖父
  - 再往里的话就是第二层 `<p>` 标签和 `<li>` 标签了，我们将其理解为父辈
    - 而第三层的 `<p>` 标签毫无疑问就是自己了（也就是父辈的儿子）

带入辈分后，我们想要选择第三层的全部p标签这一行为，就是选择父辈标签下的所有后代标签**（即li标签下的所有后代）**。

后代选择器的定义也很简单，以 `空格` 作为间隔，其格式如下：

```css
父元素 子元素（或后代） {
  属性名: 属性值;
}
```

那么回归刚刚的问题，如何只选择第三层的全部p标签？

```css
li p {
  color: red;
}
```

在上述 html代码中，我们使用了 `<li>` 标签来作为父标签，后代标签则是p标签。

这样的话，`<li>` 标签下的所有p标签都会被选择器选中。

!> 值得注意的是，使用了后代选择器后，我们无论向内如何嵌套，只要存在相同的后代标签，这些后代标签就都会被选中。

例如：

```html
<body>
  <p>我是第一层第一个</p>
  <p>我是第一层第二个</p>
  <p>我是第一层第三个</p>
  <ul>
    <p>我是第二层第一个</p>
    <p>我是第二层第二个</p>
    <li>
      <p>我是第三层第一个</p>
      <p>我是第三层第二个</p>
      <p>我是第三层第三个</p>
      <ul>
        <p>我是第四层第一个</p>
        <p>我是第四层第二个</p>
      </ul>
    </li>
  </ul>
</body>
```

效果如下：

<!-- ![后代选择器](https://s21.ax1x.com/2024/04/29/pkFZsYD.png) -->
<img src="https://s21.ax1x.com/2024/04/29/pkFZsYD.png" alt="后代选择器" class="zoomImage" />

我想选中的是第三层的所有p标签（即li中的所有p标签），可是第四层中的p标签也包含在li中，我们可以理解为li标签是第四层p标签的曾祖父。所以，第四层p标签也是li标签的后代，那么就会被选中。

?> 所以，无论你如何嵌套，只要是在 li 标签之内 p 标签都会被视为其后代，继而被选择器选中。

### 子元素选择器

子元素选择器只能选择作为某元素子元素的元素。它与后代选择器最大的不同就是元素间隔（层级）不同，后代选择器将该元素作为父元素，它所有的后代元素都是符合条件的，而子元素选择器只有相对于父元素来说的第一级子元素符合条件。

简单来讲，就是它只能选择**儿子**，而不能选择**孙子**后的辈分。

子元素选择器以 `>` 来作为间隔，其写作格式如下：

```css
父元素 > 子元素 {
    属性名: 属性值;
}
```

还是刚刚的代码，但我们将将 `<ul>` 标签作为父标签，子标签仍然为 `<p>`：

```html
<p>我是第一层第一个</p>
<p>我是第一层第二个</p>
<p>我是第一层第三个</p>
<ul>
  <p>我是第二层第一个</p>
  <p>我是第二层第二个</p>
  <li>
    <p>我是第三层第一个</p>
    <p>我是第三层第二个</p>
    <p>我是第三层第三个</p>
  </li>
</ul>
```

CSS部分代码：

```css
ul > p {
  color: red;
}
```

效果如下：
<!-- ![子元素选择器](https://s21.ax1x.com/2024/04/29/pkFZrFO.png) -->
<img src="https://s21.ax1x.com/2024/04/29/pkFZrFO.png" alt="子元素选择器" class="zoomImage" />

?> 不难发现，`<ul>` 标签内为 `<p>` 的子标签会被选中，而再向内嵌套的 `<p>` 标签则不会被选中。这就是子选择器的特性。

### 相邻兄弟选择器

相邻兄弟选择器可以选择紧接在另一元素后的元素，且二者有相同父元素。与后代选择器和子元素选择器不同的是，相邻兄弟选择器针对的元素是同级元素，且两个元素是相邻的，拥有相同的父元素。

简单来讲，相邻兄弟选择器能够选择一个相邻的同辈标签，但它只会向下选择。如果是在它上面的同辈标签，它就不会去管了。

相邻兄弟选择器以 `+` 作为间隔，其写作格式如下：

```css
指定标签 + 同辈标签（同级元素） {
    属性名: 属性值;
}
```

例如：

```html
<p>我是第一层第一个</p>
<h1>我是第一层第二个</h1>
<p>我是第一层第三个</p>
<p>我是第一层第四个</p>
```

CSS部分代码：

```css
h1 + p {
    color: red;
}
```

效果如下：

![相邻兄弟选择器](https://s21.ax1x.com/2024/04/29/pkFeK9e.png)
<!-- <img src="https://s21.ax1x.com/2024/04/29/pkFeK9e.png" alt="相邻兄弟选择器" /> -->

我们发现，根据规则，h1标签的下一个同级元素是p标签，所以它就会被选中；而“我是第一层第四个”的p标签就不会被选中，因为它并没有与h1标签相邻。同时，根据只能向下选择的规则，h1标签的上一个p标签并不会被选中。因此，在此案例中，只选中了“我是第一层第三个”那个p标签。

---

**使用 `+` 定义相邻兄弟选择器**后，它只允许存在一个兄弟标签 ，这个兄弟标签必须在它下面且需要相邻。

如果我们在**被指定的标签**和**兄弟标签**中间，插入一个非兄弟标签的标签，那么相邻兄弟标选择器就会失效。

它并不会为插入的标签添加样式 或者继续向下寻找，这就是相邻兄弟选择器的特性。

例如：

```html
<p>我是第一层第一个</p>
<h1>我是第一层第二个</h1>
<h5>如果我插足，样式就会失效</h5>
<p>我是第一层第三个</p>
<p>我是第一层第四个</p>
```

CSS部分代码：

```css
h1 + p {
    color: red;
}
```

效果如下：

![相邻兄弟选择器特性](https://s21.ax1x.com/2024/04/29/pkFu3u9.png)

?> 可以看到，如果指定标签和兄弟标签不再相邻，那么相邻兄弟选择器就失效了。

### 通用兄弟选择器

但如果我们使用 `~` 替换 `+` 来定义选择器的话，就会允许存在多个兄弟标签了。

这样即便中间存在隔断也不要紧。它仍会继续向下寻找，但不会向上。这种选择器也叫同胞选择器或一般兄弟选择器。

其写作格式如下：

```css
指定标签 ~ 同辈标签（同级元素） {
    属性名: 属性值;
}
```

那我们把代码改成：

```css
h1 ~ p {
    color: red;
}
```

效果如下：

![通用兄弟选择器](https://s21.ax1x.com/2024/04/29/pkFuIDs.png)

?> 这种选择器能够弥补相邻兄弟选择器的不足之处，即便和兄弟标签不相邻也不要紧，它会继续向下寻找兄弟标签，这就是通用选择器的特性。

## 伪类选择器

伪类选择器是CSS中一种特殊的选择器，它允许你基于元素的特定状态来选择并应用样式，而不仅仅是基于元素的标签名称、ID或者类。

伪类选择器是指那些处在特定状态的元素。伪类名可以单独使用，泛指所有元素，也可以和元素名连起来使用，特指某类元素。

常见的伪类有：
- **动态伪类（dynamic pseudo-classes）**
- 目标伪类（target pseudo-classes）
- 语言伪类（language pseudo-classes）
- 元素状态伪类（UI element states pseudo-classes）
- **结构伪类（structural pseudo-classes）**
- 否定伪类（negation pseudo-classes）

由于我们篇幅有限，我们只讲最常见且最常用的两个伪类：**动态伪类**和**结构伪类**。

?> 接下来请同学们做好准备，伪类是能够展开讲很久的知识点，所以理解起来也会有些困难哦~

---

### 结构伪类选择器

同样的，我们仍然需要选中特定的元素，但这一次不允许使用class和id。  
如果我要选中下列代码的**第三层的第一个**和**最后一个p标签**，那该怎么办呢？

```html
<p>我是第一层第一个</p>
<p>我是第一层第二个</p>
<p>我是第一层第三个</p>
<ul>
  <p>我是第二层第一个</p>
  <p>我是第二层第二个</p>
  <li>
    <p>我是第三层第一个</p>
    <p>我是第三层第二个</p>
    <p>我是第三层第三个</p>
    <p>我是第三层第四个</p>
  </li>
</ul>
```

对此，我们就可以使用伪类选择器在不创建id和类名的情况下来实现精准选择。

伪类选择器以 `指定标签` + `:` 作为间隔，其写作格式如下：

```css
指定标签:伪类 {
    属性名: 属性值;
}
```
!> 请注意！指定标签与伪类之间不能存在空格，只能用冒号隔开！否则，它将无法被选中。

根据要求，我们可以定义一个伪类选择器：

```css
li p:first-child {
    color: red;
}
```

这样定义选择器后，`<li>` 标签下的第一个子元素如果为 `<p>` 就会被选中

![伪类选择器](https://s21.ax1x.com/2024/05/02/pkkUenx.png)

和相邻兄弟选择器一样，如果被隔断（不再是第一个子元素）。那该选择器也会失效，它并不会继续向下寻找第一个p标签为其添加样式。

就像这样：

```html
<li>
  <h4>我来成为第一个元素</h4>
  <p>我是第三层第一个</p>
  <p>我是第三层第二个</p>
  <p>我是第三层第三个</p>
  <p>我是第三层第四个</p>
</li>
```

![伪类选择器](https://s21.ax1x.com/2024/05/02/pkkUdUS.png)

选中第三层最后一个p标签，选择器的具体定义也基本类似 我们只需要**修改对应的伪类**即可。

```css
li p:last-child {
    color: red;
}
```

![伪类选择器](https://s21.ax1x.com/2024/05/02/pkkUw4g.png)

和上面一样，如果我们在末尾定义一个非p标签的子元素，它不再是最后一个子元素的话 该选择器也会失效。

就像这样：

```html
<p>我是第三层第一个</p>
<p>我是第三层第二个</p>
<p>我是第三层第三个</p>
<p>我是第三层第四个</p>
<h4>我来成为最后一个元素</h4>
```

![伪类](https://s21.ax1x.com/2024/05/02/pkkaJG4.png)

---

我们将上述代码进行修改，将第二层的**p标签**修改为**li标签**。

```html
<p>我是第一层第一个</p>
<p>我是第一层第二个</p>
<p>我是第一层第三个</p>
<ul>
  <li>我是第二层第一个</li>
  <li>我是第二层第二个</li>
  <li>
    <p>我是第三层第一个</p>
    <p>我是第三层第二个</p>
    <p>我是第三层第三个</p>
    <p>我是第三层第四个</p>
  </li>
</ul>
```

在不使用 id 和 class 属性的同时，也不使用上述伪类选择器。我们仍有办法能够选中**第二层的第一个元素**

我们可以使用定位到其父元素的方式，来定义伪类选择器。

通过 `<li>` 标签来定位到它的父类 `<ul>` 标签，再通过 `<ul>` 标签来指定一个具体位置的子元素，该具体位置就是 `x` 。

**是不是感觉有点绕？没关系，我们来举个例子：**

```css
li:nth-child(x) {
    color: red;
}
```

我们以上述方式定义伪类选择器，`x` 所表示的就是第 `x` 个子元素。在此案例中，我们要求**第二层第一个**变色，那么我们就将`x` 改为 `1`。

```css
li:nth-child(1) {
    color: red;
}
```

![伪类](https://s21.ax1x.com/2024/05/02/pkk0DoV.png)

!> **请注意：**使用此伪类时，它会找到此标签的<font style="color:#ff6666;font-weight: bold;">父级</font>，以<font style="color:#ff6666;font-weight: bold;">父级</font>为基础向下寻找符合要求的元素，而不是以选中的<font style="color:#ff6666;font-weight: bold;">元素本身</font>来寻找！

所以，我们可以将上述案例理解为，我们**选中了 `<ul>` 下第一个标签为 `<li>` 的子元素**  
如果你仍然不理解我所说的含义，那么我们再来看一个案例：

```html
<ul>
  <h4>隔断</h4>
  <h4>隔断</h4>
  <li>我是第二层第一个</li>
  <li>我是第二层第二个</li>
  <li>
    <p>我是第三层第一个</p>
    <p>我是第三层第二个</p>
    <p>我是第三层第三个</p>
    <p>我是第三层第四个</p>
  </li>
</ul>
```

我们在原来的代码中**添加了两个h4标签作为隔断**，这个时候我们想定位到第一个li标签也不是没有办法，我们将 `x` 修改为 `3` 就好了。

![伪类](https://s21.ax1x.com/2024/05/02/pkkBpY8.png)

?> 我们可以很清楚的看到，第一个li标签是ul标签下的第三个子元素。所以这种伪类是根据**指定元素的父级**来寻找的。

---

当然了，想让其无视隔断也是能够做到的。我们只要将 `nth-child` 修改为 `nth-of-type` 即可。

这种选择器会通过传入**子元素标签类型**来选中元素，如果是非该子元素标签（隔断），它会无视该元素，**继续向下寻找规定的子元素标签**。

![伪类](https://s21.ax1x.com/2024/05/02/pkkBPSg.png)

?> 发现没有，这种选择器会直接**根据指定元素**来进行寻找，而不会考虑父元素。

---

除此之外，还有一些 `:nth-child(n)` 的常用公式：

| 属性值                             | 功能              |
|:-----------------------------------|:----------------|
| :nth-child(2n)                     | 偶数标签          |
| :nth-child(2n+1)；:nth-child(2n-1) | 奇数标签           |
| :nth-child(5n)                     | 找到5的倍数的标签   |
| :nth-child(n+5)                    | 找到第5个以后的标签 |
| :nth-child(-n-5)                   | 找到第5个以前的标签 |

> 提示：公式中的n取值从 0 开始。

---

### 动态伪类选择器

动态伪类选择器又称超链接伪类，是一种多用于链接的伪类选择器。

常见的动态伪类选择器如下表所示：

| 选择器    | 示例        | 示例说明            |
|-----------|-------------|---------------------|
| :link    | a:link     | 未访问过的a链接     |
| :visited | a:visited  | 访问过的a链接       |
| :hover   | div:hover  | 鼠标移入div时的效果 |
| :active  | div:active | 鼠标点击div时的效果 |
| :focus   | input:focus | 获得焦点的input     |

!> 注意：  
1、`:link` 和 `:visited` 只对a标签有效果，而 `:hover` 和 `:active` 对所有标签都有效果  
2、如果要同时设置这4个伪类，那么**必须按照link-visited-hover-active的顺序**（即LVHA）

例如：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>动态伪类选择器</title>
  <style>
    a:link{
        color: red;
    }
    a:visited{
        color: brown;
    } 
    a:hover{
        color: orange;
    }
    a:active{
        color: purple;
    }
  </style>
</head>
<body>
  <a href="#">我是鲶大禹</a>  
</body>
</html>
```

这是未点击链接的效果：

![动态伪类](https://s21.ax1x.com/2024/05/03/pkkzgOS.png)

鼠标移入时的链接效果：

![动态伪类](https://s21.ax1x.com/2024/05/03/pkkzWwQ.png)

鼠标按下后的链接效果：

![动态伪类](https://s21.ax1x.com/2024/05/03/pkkzOw4.png)

访问过链接后的效果：

![动态伪类](https://s21.ax1x.com/2024/05/03/pkkzxYR.png)

是不是分别对应了css代码中设置的 `link` 、`hover` 、`active` 、`visited`

foucus属性一般用于输入框，当输入框获得焦点时，将会运用样式。

举个例子：

```css
input:focus {
  background-color: red;
}
```

```html
<input type="text">
```

这是未获得焦点时的效果：

![焦点](https://s21.ax1x.com/2024/05/03/pkASu1P.png)

当你选中这个输入框时：

![焦点](https://s21.ax1x.com/2024/05/03/pkASMX8.png)

现在是不是就清晰很多啦~

## 伪元素选择器

伪元素是指那些元素中特别的内容，与伪类不同的是，伪元素表示的是元素内部的东西，逻辑上存在，但在文档树中并不存在与之对应关联的部分。伪元素选择器的格式与伪类选择器一致。

**CSS3 伪元素选择器注意事项：**
- content 属性：上述两个选择器 **必须设置 content 属性**；
- 元素类型：伪元素选择器默认添加的是 **行内元素**；
  - 如果要为其配置宽高，需要 **将显示模式 display 转为块级元素 block 或 行内块元素 inline-block**；
- 伪元素本质：在 dom 中看不到插入的元素；
- 权重：伪元素选择器 的权重与 标签选择器 权重相同，权重为 1；

**区分 伪元素选择器 与 伪类选择器：**
- **伪类选择器有一个冒号**，如 `a:hover` 表示鼠标经过 a 标签上的样式；
- **伪元素选择器有两个冒号**；

**常见的伪元素选择器有：**

| 伪元素名           | 含义             |
|----------------|----------------|
| ::first-letter | 向文本的第一个字母添加样式  |
| ::first-line   | 向文本的第一行添加样式    |
| ::after        | 在元素之后添加内容      |
| ::before       | 在元素之前添加内容      |

说了这么多，我们还是要看个案例来深入理解它的用法：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>伪元素选择器</title>
  <style>
    div {
      width: 400px;
      height: 200px;
      border: 1px solid red;
      background-color: pink;
    }
    
    div::before {
      /* 在盒子前面插入的元素 */
      content: "div::before 盒子前面插入内容";
      /* 插入的内容默认为行内元素 
          可以转为块级元素 和 行内块元素 */
      display: block;
      width: 300px;
      height: 20px;
      background-color: aqua;
    }
    
    div::after {
      /* 在盒子后面插入的元素 */
      content: "div::after 盒子后面插入内容";
      /* 插入的内容默认为行内元素 
          可以转为块级元素 和 行内块元素 */
      display: block;
      width: 300px;
      height: 20px;
      background-color: yellow;
    }
  </style>
</head>
<body>
  <div>盒子原有内容</div>
</body>
</html>
```

效果如下：

<!-- ![伪元素](https://s21.ax1x.com/2024/05/03/pkApw8I.png) -->
<img src="https://s21.ax1x.com/2024/05/03/pkApw8I.png" alt="伪元素" class="zoomImage70" />

我们发现，在使用伪元素选择器后，调试界面中并没有与之对应的元素，这也是一开始讲到的**文档树（dom）中并不存在与之对应关联的部分**的含义。

---

## 属性选择器