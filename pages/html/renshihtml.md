# 认识HTML语言

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>鲶大禹的笔记</title>
    </head>
    <body>
    
        <h1>我的第一个标题</h1>
        
        <p>我的第一个段落。</p>
    
    </body>
</html>
```

HTML 是用来描述网页的一种语言。
- HTML 指的是超文本标记语言: **H**yper**T**ext **M**arkup **L**anguage
- HTML 不是一种编程语言，而是一种**标记**语言
- 标记语言是一套**标记标签** (markup tag)
- HTML 使用标记标签来**描述**网页
- HTML 文档包含了HTML **标签**及**文本**内容
- HTML 文档也叫做 **web 页面**

# 实例解析

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/18/pFJWXTI.png" alt="实例解析" width="85%">
</div>

- `<!DOCTYPE html>` 声明为 HTML5 文档
- `<html>` 元素是 HTML 页面的根元素
- `<head>` 元素包含了文档的元（meta）数据，如 `meta charset="utf-8"` 定义网页编码格式为 utf-8
- `<title>` 元素描述了文档的标题
- `<body>` 元素包含了可见的页面内容
- `<h1>` 元素定义一个大标题
- `<p>` 元素定义一个段落

**注：**在浏览器的页面上使用键盘上的 <kbd>F12</kbd> 按键开启调试模式，就可以看到组成标签。

!> 值得注意的是，在编写代码的时候，要保证代码的<font style="color:#42b983;font-weight:bold;">格式化</font>，如上述给出的范例一致：

- `<head>` 标签是包含在 `<html>` 标签中的； `<body>` 标签同样是包含在 `<html>` 标签中的，与 `<head>` 标签同级。 
- 而剩下的内容，则都是包含在 `<body>` 或 `<head>` 标签中的。

而更多格式化的内容，我们将在下个章节讲述。

# 格式化

为保证代码的可读性，我们通常会在有包含关系的代码前加入缩进字符。**（这是重点嗷！！）**  
就像这样：

```html
<html>
    <head>
        <style>
        </style>
    </head>

    <body>
        <div>
            <img src="鲶大禹" alt="的笔记">
        </div>
    </body>
</html>
```

在上述代码中， `<head>` 标签与 `<body>` 标签都是包含在 `<html>` 标签中的，而 `<style>` 标签则是包含在 `<head>` 标签中的。所以，在这些代码前，我加了缩进来表示包含关系。  
缩进可以是两个空格，也可以是四个空格，甚至可以是空格与制表符 <kbd>Tab</kbd> 的混合。但使用缩进的最终目的，都将是使代码的可读性最大化。

# HTML标签

HTML 标记标签通常被称为 HTML 标签 (HTML tag)。
- HTML 标签是由尖括号包围的关键词，比如 `<html>`
- HTML 标签通常是成对出现的，比如 `<b>` 和 `</b>`
- 标签对中的第一个标签是开始标签，第二个标签是结束标签
- 开始和结束标签也被称为开放标签和闭合标签
- 有些标签不需要结束标签，比如 `<img>` 标签。

```html
<标签>内容</标签>
```

?> 需要注意的是，若不是单标签，那就必须存在闭合标签，否则就可能出现不生效的问题。

# HTML网页结构

这是一个可视化的HTML页面结构：  
![网页结构](https://s11.ax1x.com/2024/02/18/pFJoeQf.png)

!> 	只有 `<body>` 区域（白色部分）才会在浏览器中显示。

# <!DOCTYPE> 声明

`<!DOCTYPE>` 声明有助于浏览器中正确显示网页。

网络上有很多不同的文件，如果能够正确声明HTML的版本，浏览器就能正确显示网页内容。

`doctype` 声明是不区分大小写的，以下方式均可：

```html
<!DOCTYPE html>
<!DOCTYPE HTML>
<!doctype html>
<!Doctype Html>
```

> 关于其他更多的DOCTYPE声明，将不再在此赘述。