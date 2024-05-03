# HTML进阶

在本章节中，我们即将开始学习<font style="color: #42b983;font-weight: bold">列表、表格、表单</font>，并熟练掌握它们。

> 目标：掌握嵌套关系标签的写法，使用列表标签布局网页

## 01 - 列表

作用：布局内容排列整齐的区域。

列表分类：无序列表、有序列表、定义列表。

### 无序列表

作用：布局排列整齐的**不需要规定顺序**的区域。

标签：ul 嵌套 li，ul 是无序列表，li 是列表条目。

```html
<ul>
  <li>第一项</li>
  <li>第二项</li>
  <li>第三项</li>
  ……
</ul>
```

浏览器显示如下：

- 第一项
- 第二项
- 第三项

> 注意事项：
>
> * ul 标签里面只能包裹 li 标签
> * li 标签里面可以包裹任何内容

### 有序列表

作用：布局排列整齐的**需要规定顺序**的区域。

标签：ol 嵌套 li，ol 是有序列表，li 是列表条目。

```html
<ol>
  <li>第一项</li>
  <li>第二项</li>
  <li>第三项</li>
  ……
</ol>
```
浏览器显示如下：

1. 第一项
2. 第二项
3. 第三项

> 注意事项：
>
> * ol 标签里面只能包裹 li 标签
> * li 标签里面可以包裹任何内容

### 定义列表

标签：dl 嵌套 dt 和 dd，dl 是定义列表，dt 是定义列表的标题，dd 是定义列表的描述 / 详情。

```html
<dl>
  <dt>列表标题</dt>
  <dd>列表描述 / 详情</dd>
   ……
</dl>
```
浏览器显示如下：

<dl>
  <dt>列表标题</dt>
  <dd>- 列表描述 / 详情</dd>
</dl>

**像小米的官网：**

<!-- ![样例](https://s21.ax1x.com/2024/03/22/pFhZkzF.png) -->
<img src="https://s21.ax1x.com/2024/03/22/pFhZkzF.png" alt="样例" width="80%" >

> 注意事项：
>
> * dl 里面只能包含dt 和 dd
> * dt 和 dd 里面可以包含任何内容

## 02 - 表格

网页中的表格与 Excel 表格类似，用来展示数据。 

HTML 表格是一种用于展示结构化数据的标记语言元素。

![样例](https://s21.ax1x.com/2024/03/22/pFhZgwn.png)

### 基本使用

标签：table 嵌套 tr，tr 嵌套 td / th。

每个表格均有若干行（由 `<tr>` 标签定义），每行被分割为若干单元格（由 `<td>` 标签定义），表格可以包含标题行（ `<th>` ）用于定义列的标题。

- tr：tr 是 table row 的缩写，表示表格的一行。
- td：td 是 table data 的缩写，表示表格的数据单元格。
- th：th 是 table header的缩写，表示表格的表头单元格（居中并加粗）。

数据单元格可以包含**文本、图片、列表、段落、表单、水平线、表格**等等。

> 提示：在网页中，**表格默认没有边框线**，使用 **border 属性**可以为表格添加边框线。 

```html
<table border="1">
  <tr>
    <th>姓名</th>
    <th>语文</th>
    <th>数学</th>
    <th>总分</th>
  </tr>
  <tr>
    <td>张三</td>
    <td>99</td>
    <td>100</td>
    <td>199</td>
  </tr>
  <tr>
    <td>李四</td>
    <td>98</td>
    <td>100</td>
    <td>198</td>
  </tr>
  <tr>
    <td>总结</td>
    <td>全市第一</td>
    <td>全市第一</td>
    <td>全市第一</td>
  </tr>
</table>
```

在浏览器显示如下：
<table>
  <tr>
    <th>姓名</th>
    <th>语文</th>
    <th>数学</th>
    <th>总分</th>
  </tr>
  <tr>
    <td>张三</td>
    <td>99</td>
    <td>100</td>
    <td>199</td>
  </tr>
  <tr>
    <td>李四</td>
    <td>98</td>
    <td>100</td>
    <td>198</td>
  </tr>
  <tr>
    <td>总结</td>
    <td>全市第一</td>
    <td>全市第一</td>
    <td>全市第一</td>
  </tr>
</table>

### 表格结构标签

作用：用表格结构标签把内容划分区域，让表格结构更清晰，语义更清晰。

| **标签名** | **含义** | **特殊说明** |
|:-------:|:------:|:---------:|
| thead   | 表格头部   | 表格头部内容    |
| tbody   | 表格主体   | 主要内容区域    |
| tfoot   | 表格底部   | 汇总信息区域    |

**`<thead>` 用于定义表格的标题部分:** 在 `<thead>` 中，使用 `<th>` 元素定义列的标题。

**`<tbody>` 用于定义表格的主体部分:** 在 `<tbody>` 中，使用 `<tr>` 元素定义行，并在每行中使用 `<td>` 元素定义单元格数据。

HTML 表格还可以具有其他部分，如 `<tfoot>` （表格页脚）和 `<caption>` （表格标题），`<tfoot>` 可用于在表格的底部定义摘要、统计信息等内容。 `<caption>` 可用于为整个表格定义标题。

需要注意的是，`<caption>` 标签必须放置在 `<table>` 标签内，否则将无法定位到表格。

例如：

<table>
  <caption>XXX学校排名</caption>
  <tr>
    <th>姓名</th>
    <th>语文</th>
    <th>数学</th>
    <th>总分</th>
  </tr>
  <tr>
    <td>张三</td>
    <td>99</td>
    <td>100</td>
    <td>199</td>
  </tr>
  <tr>
    <td>李四</td>
    <td>98</td>
    <td>100</td>
    <td>198</td>
  </tr>
  <tr>
    <td>总结</td>
    <td>全市第一</td>
    <td>全市第一</td>
    <td>全市第一</td>
  </tr>
</table>

> 提示：表格结构标签可以省略。

### 合并单元格

作用：将多个单元格合并成一个单元格，以合并同类信息。 

![样例](https://s21.ax1x.com/2024/03/22/pFhe61O.png)

合并单元格的步骤：

1. 明确合并的目标
2. 保留**最左最上**的单元格，添加属性（取值是**数字**，表示需要**合并的单元格数量**）
   * **跨行合并**，保留最上单元格，添加属性 **rowspan**
   * **跨列合并**，保留最左单元格，添加属性 **colspan**
3. 删除其他单元格

```html
<table border="1">
  <thead>
    <tr>
      <th>姓名</th>
      <th>语文</th>
      <th>数学</th>
      <th>总分</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>张三</td>
      <td>99</td>
      <td rowspan="2">100</td>
      <td>199</td>
    </tr>
    <tr>
      <td>李四</td>
      <td>98</td>
      <td>198</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>总结</td>
      <td colspan="3">全市第一</td>
    </tr>
  </tfoot>
</table>
```

<table>
  <thead>
    <tr>
      <th>姓名</th>
      <th>语文</th>
      <th>数学</th>
      <th>总分</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>张三</td>
      <td>99</td>
      <td rowspan="2">100</td>
      <td>199</td>
    </tr>
    <tr>
      <td>李四</td>
      <td>98</td>
      <td>198</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>总结</td>
      <td colspan="3">全市第一</td>
    </tr>
  </tfoot>
</table>

> 注意：不能跨表格结构标签合并单元格（thead、tbody、tfoot）。

## 03 - 表单

作用：收集用户信息。

使用场景：

* 登录页面
* 注册页面
* 搜索区域

HTML 表单表示文档中的一个区域，此区域包含交互控件，将用户收集到的信息发送到 Web 服务器。

HTML 表单通常包含各种输入字段、复选框、单选按钮、下拉列表等元素。

- `<form>` 元素用于创建表单，action 属性定义了表单数据提交的目标 URL，method 属性定义了提交数据的 HTTP 方法。
- `<label>` 元素用于为表单元素添加标签，提高可访问性。
- `<input>` 元素是最常用的表单元素之一，它可以创建文本输入框、密码框、单选按钮、复选框等。type 属性定义了输入框的类型，id 属性用于关联 `<label>` 元素，name 属性用于标识表单字段。
- `<select>` 元素用于创建下拉列表，而 `<option>` 元素用于定义下拉列表中的选项。

### form 标签

!> 所有表单元素都应放在 `<form>` 标签中，否则部分功能可能无法使用。

```html
<form>
  <input type="text" name="NDYian" />
</form>
```

### input 标签

input 标签 type 属性值不同，功能就会不同。 

```html
<input type="属性值" >
```

| **type属性值** | **说明**       |
|:-----------:|:-------------:|
| text        | 文本框，用于输入单行文本  |
| password    | 密码框           |
| radio       | 单选框           |
| checkbox    | 多选框           |
| file        | 上传文件          |

**`text` 属性所呈现的效果：**
<input type="text" >

**`password` 属性所呈现的效果：**
<input type="password" placeholder="输入后应该是小圆点" >

**`radio` 属性所呈现的效果：**
<input type="radio" id="male" name="gender"><lable for="male">男</lable>
<input type="radio" id="male" name="gender"><lable for="male">女</lable>

**`checkbox` 属性所呈现的效果：**
<input type="checkbox" id="male"><lable for="male">男</lable>
<input type="checkbox" id="male"><lable for="male">女</lable>

**`file` 属性所呈现的效果：**
<input type="file" >

---

当然，我们还可以使用 `required` 属性 来设置必填项。  
例如：

```html
<form action="#">
  <input type="text" required>
  <input type="submit" value="提交">
</form>
```

**在浏览器中呈现的效果：**
<form action="#">
  <input type="text" required>
  <input type="submit" value="提交">
</form>

?> 现在，如果输入框为空，则提交按钮将会不起效果。

---

除此之外，type的属性值还有：

| **type属性值** | **说明**       |
|:-----------:|:-------------:|
| range       | 滑动条         |
| color       | 颜色选择器     |
| date        | 日期选择器     |
| datetime    | 日期和时间选择器 |
| datetime-local | 本地日期和时间选择器 |
| month       | 月份选择器     |
| time        | 时间选择器     |
| url         | URL地址输入框   |
| number      | 数字输入框     |
| search      | 搜索框         |

> 其效果我将不再在此赘述。

---

### input 标签占位文本 

占位文本：提示信息，文本框和密码框都可以使用。 

```html
<input type="..." placeholder="提示信息">
```

### 单选框

常用属性

| **属性名** | **作用** | **特殊说明**            |
|:-------:|:------:|:--------------------:|
| name    | 控件名称   | 空间分组，同组只能选中一个（单选功能）  |
| checked | 默认选中   | 属性名和属性值相同，简写为一个单词    |


```html
<input type="radio" name="gender" checked> 男
<input type="radio" name="gender"> 女
```

在浏览器中展现的效果：
<input type="radio" name="gender" checked> 男
<input type="radio" name="gender"> 女

?> 默认选中了“男”选项。

> 提示：name 属性值自定义。
> 
> 当 name 的值相同时，则可以实现单选效果。

### 上传文件 

默认情况下，文件上传表单控件只能上传一个文件，添加 `multiple` 属性可以实现文件多选功能。

```html
<input type="file" multiple>
```
在浏览器中呈现的效果：
<input type="file" multiple>

!> 与刚刚所提到的上传文件的效果有什么区别呢？

刚刚的效果：
<input type="file" >

!> 你会发现，当运用了 `multiple` 属性时，按住 `ctrl` 键，可以同时选择多个文件。

### 多选框

多选框也叫复选框，默认选中：checked。

```html
<input type="checkbox" checked> 鲶大禹的笔记本
```

浏览器中呈现的效果：
<input type="checkbox" checked> 鲶大禹的笔记本

### 下拉菜单

![下拉菜单](https://s21.ax1x.com/2024/03/30/pFTVanS.png)

标签：select 嵌套 option，select 是下拉菜单整体，option是下拉菜单的每一项。

```html
<select>
  <option>北京</option>
  <option>上海</option>
  <option>广州</option>
  <option>深圳</option>
  <option selected>武汉</option>
</select>
```

> 默认显示第一项，**selected** 属性实现**默认选中**功能。

在浏览器中呈现的效果：
<select>
  <option>北京</option>
  <option>上海</option>
  <option>广州</option>
  <option>深圳</option>
  <option selected>武汉</option>
</select>

当然，我们还可以使用 `optgroup` 标签，实现分组功能。

例如：
```html
<select>
  <optgroup label="1">
    <option value="">临汾</option>
    <option value="">太原</option>
  </optgroup>
  <optgroup label="2">
    <option value="">昆山</option>
    <option value="">江苏</option>
  </optgroup>
</select>
```

在浏览器中呈现的效果：
<select>
  <optgroup label="1">
    <option value="">临汾</option>
    <option value="">太原</option>
  </optgroup>
  <optgroup label="2">
    <option value="">昆山</option>
    <option value="">江苏</option>
  </optgroup>
</select>

?> 在上述案例中，我们使用了optgroup标签，设置了分组，而每个分组的label属性值就是分组名称。

在下拉框中同样可以使用 `multiple` 属性，表示多选。  
例如：

```html
<select multiple>
  <option>北京</option>
  <option>上海</option>
  <option>广州</option>
  <option>深圳</option>
  <option selected>武汉</option>
  <option>西安</option>
  <option>成都</option>
</select>
```

**在浏览器中呈现的效果：**

<select multiple>
  <option>北京</option>
  <option>上海</option>
  <option>广州</option>
  <option>深圳</option>
  <option>武汉</option>
  <option>西安</option>
  <option>成都</option>
</select>

现在，当你按住 <kbd>Ctrl</kbd> 键时，就可以选择多个选项了。

### 文本域

作用：多行输入文本的表单控件。 

![文本域](https://s21.ax1x.com/2024/03/30/pFTVypq.png)

```html
<textarea>鲶大禹的笔记</textarea>
```

在浏览器中呈现的效果：

<textarea>鲶大禹的笔记</textarea>

> 注意点：
>
> * 实际开发中，使用 CSS 设置 文本域的尺寸
> * 实际开发中，一般禁用右下角的拖拽功能

当然，多行文本域还有以下几个属性你需要掌握：
1. `cols` ：垂直列。在没有做样式表设置的情况下，它表示一行中可容纳下的字节数。例如 `cols=60` ，表示一行中最多可容纳60个字节，也就是30个汉字。另外要注意的是，文本框的宽度就是由这个属性来调整。
2. `rows` ：水平列。表示可显示的行数，例如 `rows=10` ，表示可显示10行。超过10行，则需要拖动滚动条来浏览了。（同上，文本框的高度就是通过这个来控制的。）
3. `name` ：文本框的名称，这项必不可省，因为存储文本的时候必须用到。

```html
<textarea cols="30" rows="10" name="content">鲶大禹的笔记</textarea>
```

在浏览器中呈现的效果：

<textarea cols="30" rows="10" name="content">鲶大禹的笔记</textarea>

顺带提一嘴，若要取消文本域的拖拽，则需要用到css样式。

```css
textarea {
  resize: none;
}
```

在浏览器中呈现的效果：

<textarea cols="30" rows="2" name="content" style="resize: none;">鲶大禹的笔记</textarea>



### label 标签 

作用：网页中，某个标签的说明文本。 

经验：用 label 标签绑定文字和表单控件的关系，增大表单控件的点击范围，以获得更好的体验。

![label](https://s21.ax1x.com/2024/03/30/pFTV71x.png)

* 写法一
  * label 标签只包裹内容，不包裹表单控件
  * 设置 label 标签的 for 属性值 和表单控件的 id 属性值相同

```html
<input type="radio" id="man">
<label for="man">男</label>
```

在浏览器中呈现的效果：

<input type="radio" id="man">
<label for="man">男</label>

?> 当你点击“男”这个字的时候，是不是也可以选中这个选项啦

* 写法二：使用 label 标签包裹文字和表单控件，不需要属性 

```html
<label><input type="radio">女</label>
```

<label><input type="radio">女</label>

?> 效果是一样哒~

> 提示：支持 label 标签增大点击范围的表单控件：文本框、密码框、上传文件、单选框、多选框、下拉菜单、文本域等等。 

### 按钮

```html
<button type="">按钮</button>
```

| **type属性值** | **说明**                         |
|:-----------:|:-------------------------------:|
| submit      | 提交按钮，点击后可以提交数据到后台（默认功能）         |
| reset       | 重置按钮，点击后将表单控件恢复默认值  |
| button      | 普通按钮，默认没有功能，一般配合JavaScript使用    |


```html
<!-- form 表单区域 -->
<!-- action="" 发送数据的地址 -->
<form action="">
  用户名：<input type="text">
  <br><br>
  密码：<input type="password">
  <br><br>

  <!-- 如果省略 type 属性，功能是 提交 -->
  <button type="submit">提交</button>
  <button type="reset">重置</button>
  <button type="button">普通按钮</button>
</form>
```

在浏览器中呈现的效果：

<form action="">
  用户名：<input type="text">
  <br><br>
  密码：<input type="password">
  <br><br>

  <!-- 如果省略 type 属性，功能是 提交 -->
  <button type="submit">提交</button>
  <button type="reset">重置</button>
  <button type="button">普通按钮</button>
</form>

?> 当你按下“提交”按键后，默认会提交表单数据到后台，并刷新网页。

!> `input` 标签也可以使用以上三个type属性值，用法相同，无任何区别。但 `button` 标签对于功能性来讲会更多且更实用。

> 提示：按钮需配合 form 标签（表单区域）才能实现对应的功能。

## 04 - 语义化

### 无语义的布局标签 

作用：布局网页（划分网页区域，摆放内容）

* div：独占一行
* span：不换行

```html
<div>div 标签，独占一行</div>
<span>span 标签，不换行</span>
```

### 有语义的布局标签

| **标签名** | **语义** |
|:-------:|:-------:|
| header  | 网页头部    |
| nav     | 网页导航    |
| footer  | 网页底部    |
| aside   | 网页侧边栏   |
| section | 网页区块    |
| article | 网页文章    |

> 语义标签用作在大网站中，可以更好的理清网页结构。

## 05 - 字符实体

有的时候，我们在网页中不能直接打出特殊字符。当我们在网页中打出一个标签，类似于 `<p>` 。如果你想让他显示在网页中而不是当做标签，那就需要用到字符实体。

例如：
```html
&lt;p&gt;
```

在浏览器中呈现的效果：

&lt;p&gt;

这样就能完整的显示出 `<p>` 标签了。

| **显示结果** | **描述** | **实体名称** |
|:--------:|:------:|:---------:|
|          | 空格     | `&nbsp;`    |
| <        | 小于号    | `&lt;`      |
| >        | 大于号    | `&gt;`      |

?> 恭喜！到此为止，你已经学完了 HTML 的全部基础部分。接下来请继续学习 CSS 样式表。