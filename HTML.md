# HTML

## 1 简介

HyperText Markup Language超文本标记语言

浏览器能解析HTML建立的WEB站点

文档后缀：.htm, .html

## 2 元素

开始标签+元素内容+结束标签

空内容/在开始标签中关闭

元素有属性

元素通常嵌套

## 3 属性

元素的附加信息，在开始标签中

name="value"

| 属性名   | 说明                   | 属性名  | 说明                          |
| -------- | ---------------------- | ------- | ----------------------------- |
| id       | 标识符                 | class   | css/js类名                    |
| style    | CSS样式                | title   | （悬停）信息                  |
| data-*   | js自定义数据           | href    | a/link中url                   |
| src      | img/script/iframe的url | alt     | img的替代文本                 |
| type     | input/button的类型     | value   | input/button/checkbox的初始值 |
| disabled | 禁用表单交互           | checked | 是否被选中                    |

## 4 标题

标题\<h1\>~\<h6\>

水平线\<hr\>

注释\<!--xxx--\>

## 5 段落

段落\<p\>xxx\</p\>

折行\<p>xxx\<br\>xxxx\</p\>

## 6 格式化标签

\<b>加粗\</b\>

\<i>斜体\</i\>

\<sub/sup>上标/下标\</sub/sup\>

## 7 链接

a-anchor

\<a href="URL"\>链接文本\<\a\>

## 8 头部

头部元素

| 标签  | 说明                   | 标签   | 说明             |
| ----- | ---------------------- | ------ | ---------------- |
| title | 标题                   | base   | 默认链接         |
| link  | 链接到样式表等         | style  | 样式或样式的地址 |
| meta  | 元数据：关键词，作者等 | script | 脚本             |

*元素和属性可能同名，但功能不同

##  9 CSS

渲染元素标签的样式

## 10 图像

 \<img src="url" alt="text" width="xxx" height="xxx"\>

\<map> 图像地图

\<area\> 图像地图中的可点击区域

## 11 表格

```
<table>	表格标签
	<thead>	表格标题
		<tr> table row 表格的一行
			<th>xx</th> table header表格表头的一格
		<\tr>
	</thead>
	<tbody> 表格主体
		<tr> table row 表格的一行
			<td>xx</td> table data表格数据的一格
		<\tr>
	</tbody>
</table>
```

## 12 列表

无序列表：

```
<ul> unordered list无序列表标签
	<li>xxx</li> list item 列表项目
</ul>
```

有序列表

```
<ol> ordered list
	<li></li>
</ol>
```

自定义列表

```
<dl> definition list 定义列表
	<dt>xxx</dt> definition term 定义术语
	<dd>xxx</dd> definition description 定义描述
</dl>
```

## 13 区块

\<div\> 块级，定义文档区域

\<span\> 内联，组合行内元素

## 14 布局

用\<div\>将整个网页划分成多个列

## 15 表单和输入

| 标签     | 说明                      | 标签     | 说明                  |
| -------- | ------------------------- | -------- | --------------------- |
| form     | 最外层，定义表单          | input    | 定义输入域            |
| textarea | 定义文本域（多行）        | label    | 输入标题，在input外层 |
| fieldset | 一组相关表单元素          | legend   | fieldset的标题        |
| select   | 下拉选项列表,在option外层 | optgroup | 选项组                |
| option   | 下拉列表的选项            | button   | 点击按钮              |
| datalist | 输入选项                  | keygen   | 密钥对生成器          |
| output   | 计算结果                  |          |                       |

