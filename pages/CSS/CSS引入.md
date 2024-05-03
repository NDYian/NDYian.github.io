# CSS 的引入方式

CSS 样式表可以增强 HTML 文档的显示效果，为了在 HTML 中使用 CSS 样式表，通常有以下4种方式：

## 引入外部样式文件

通过 `<link>` 元素引入外部样式文件，外部样式文件通常是 CSS 后缀的文件，这种方式的优点是样式文件与 HTML 文档分离，一份样式文件可以用于多份 HTML 文档，重用性较好。

其基本格式如下：
```html
<link type="text/css" rel="stylesheet" href="CSS文件URL">
```

> `rel` 在这里所表示的含义就是声明你链接过来的文件是 CSS样式表，告诉浏览器这是一个样式文件。

## 导入外部样式文件

通过 `<style>` 元素使用 `@import` 导入，效果与引入外部样式文件相同。

其基本格式如下：
```html
<style>
    @import "CSS文件URL";
</style>
```

## 使用内部样式定义

直接将 CSS 样式表写在 `<style>` 元素中作为元素的内容。这种写法重用性差，有时还会导致 HTML 文档过大。当重复的 CSS 代码在不同的 HTML 文档中存在时，必然导致大量的重复下载。在希望某些 CSS 仅对某个页面有效时，通常会采用这种形式。

?> 在我们刚学习 CSS 时，将会使用此方法。此方法常用于学习。

其基本格式如下：

```html
<style>
    div {
        background-color: pink;
        width: 400px;
        height: 400px;
    }
</style>
```

## 使用内联样式定义

将 CSS 样式表写到元素的通用属性 `style` 中，这种方式只对单个元素有效，不会影响整个文件，可以精准地控制 HTML 文档的显示效果。

其基本格式如下：

```html
<div style="color: red; font-size:20px;">这是 div 标签</div>
```

?> **总结一下：**外部样式常用于开发中，内部样式则常用作学习中，而内联样式（行内样式）常配合 JavaScript 使用。