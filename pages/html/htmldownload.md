# 前期准备

在此，我极力推荐使用 [VScode](https://code.visualstudio.com/)来编写程序。

# 下载软件

因VScode服务器在美国，下载速度特别慢。如果你下载时速度特别慢，那么请使用以下方法更改为国内镜像地址：

1. 在官网点击下载后，暂停下载并找到下载地址。如下图所示：
![下载链接](https://s11.ax1x.com/2024/02/19/pFJqzQI.png)
2. 右键复制下载链接。
3. 将下载链接粘贴到导航栏中。注意，我们需要将链接中的 `az764295.vo.msecnd.net` 替换为国内镜像地址：`vscode.cdn.azure.cn`  
即 `https://az764295.vo.msecnd.net/stable/129500ee4c8ab7263461ffe327268ba56b9f210d/VSCodeUserSetup-x64-1.72.1.exe`  
修改为 `https://vscode.cdn.azure.cn/stable/129500ee4c8ab7263461ffe327268ba56b9f210d/VSCodeUserSetup-x64-1.72.1.exe`
4. 下载完成后一直默认下一步安装即可。

!> **2024年2月19日测试：**官网下载地址未出现速度过慢问题，可以直接从官网下载。

# 插件安装

由于VScode可编写多种语言，所以需要安装相应的插件来保证更好的开发体验。  
在本次教程中，我们所编写的语言是 `HTML`，所以需要安装 `HTML` 的相应插件。

## 插件商城
在初次打开VScode时，界面是全英文的。我们需要打开插件商城来下载中文补丁，来使我们的VScode界面更加友好。

点击左侧的插件图标，进入插件商店：

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJOe4e.jpg" width="70%">
</div>

你可以在上方搜索框中搜索插件：

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJLwTO.png" width="25%">
</div>

在搜索到插件后点击 `安装` 或 `install` 即可。

## Chinese (Simplified)

此插件可以将VScode界面汉化，以保证你更好的开发体验。在安装完毕后，根据**右下角**提示重启VScode即可。

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJLLn0.png" width="70%">
</div>

## Auto Rename Tag

此插件可以自动修改标签名，在修改开始标签时，结束标签也会一同更改。

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJLbXq.png" width="70%">
</div>

## Auto Close Tag

此插件可以自动闭合标签，在打出开始标签后会自动跟上结束标签，避免了手动闭合标签的麻烦。

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJLHcn.png" width="70%">
</div>

## Live Server

此插件可以在保存代码的时候自动刷新网页预览，方便我们进行预览，也养成了随手 <kbd>**Ctrl**</kbd> **+** <kbd>**S**</kbd> 保存的习惯。

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJL71s.png" width="70%">
</div>

## Prettier

此插件可以自动格式化代码，使代码更加规范。

!> 注意！此插件<font style="color:#ff6666;font-weight: bold;">非常不推荐</font>初学者使用。在刚开始学习时，我们必须自己熟练掌握代码的格式化，而不是借助插件。

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJLTpj.png" width="70%">
</div>

安装好这个插件后，我们需要做几个简单的设置才能使此插件生效。

按下 <kbd>**Ctrl**</kbd> **+** <kbd>**,**</kbd> 或点击左下角小齿轮打开设置。

依次点击 `文本编辑器` > `格式化` > `Formate On Save`。

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJOZND.png" width="70%">
</div>

设置完后，回到VScode界面，打开任意一个html文件，右键空白处，选择 `使用…格式化文档`。

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJOlut.png" width="70%">
</div>

然后选择 `配置默认格式化程序…` > `Prettier - Code formatter` 即可完成设置。

<div align="center">
    <img src="https://s11.ax1x.com/2024/02/19/pFJOJUS.png" width="70%">
</div>

?> 现在，当你按下 <kbd>**Ctrl**</kbd> **+** <kbd>**S**</kbd> 时，代码就会自动格式化啦~

# VScode 快捷键

## 快速复制一行

将光标移至需要复制的行，按下如下快捷键即可复制：  
<font style="color:#42b983;font-weight: bold;">快捷键：</font><kbd>**Shift**</kbd> **+** <kbd>**alt**</kbd> **+** <kbd>**↑**</kbd> / <kbd>**↓**</kbd>

<div align="center">
    <img src="https://pic.imgdb.cn/item/65d24e029f345e8d03ce3ae8.gif">
</div>

## 选定多个相同的单词

<font style="color:#42b983;font-weight: bold;">快捷键：</font><kbd>**Ctrl**</kbd> **+** <kbd>**D**</kbd>
先双击选定一个单词，然后按下 <kbd>**Ctrl**</kbd> **+** <kbd>**D**</kbd> 可以往下依次选择相同的单词。这样同时修改相同的单词就非常方便。

<div align="center">
    <img src="https://pic.imgdb.cn/item/65d24e029f345e8d03ce3a91.gif">
</div>

## 添加多个光标

<font style="color:#42b983;font-weight: bold;">快捷键：</font><kbd>**Ctrl**</kbd> **+** <kbd>**Alt**</kbd> **+** <kbd>**↑**</kbd> / <kbd>**↓**</kbd>

<div align="center">
    <img src="https://pic.imgdb.cn/item/65d24e029f345e8d03ce3b18.gif" width="50%">
</div>

## 选择某个区块

可以选择一个区块进行操作。  
<font style="color:#42b983;font-weight: bold;">快捷键：</font><kbd>**Shift**</kbd> **+** <kbd>**Alt**</kbd> **+** <kbd>**拖动鼠标**</kbd>

<div align="center">
    <img src="https://pic.imgdb.cn/item/65d24e029f345e8d03ce39b9.gif">
</div>