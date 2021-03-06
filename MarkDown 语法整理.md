# MarkDown 语法整理

[TOC]生成目录

## 标题

# 这是一阶标题
## 这是二阶标题
### 这是三阶标题
#### 这是四阶标题
##### 这是五阶标题
###### 这是六阶标题

## 引用

	这是一个代码区块
	
> 引用段落
> > 嵌套的引用段落
> > > 嵌套的嵌套
	
## 列表

* 无序列表
+ 无序列表
- 无序列表

1. 有序列表
2. 有序列表
3. 有序列表

- 列表包含多个段落，子段落前用一个`tab`缩进

	这是第二段
	
	这是第三段
	
- 列表包含引用，代码区块前用两个`tab`缩进，引用段落需要一个`tab`加上一个`>`符号

		代码区块
		
	> 引用段落

## 分割线

在一行里面用三个`*`、`-`、`_`来表示分割线，这一行不可以包含其他内容

***

___
 
---

## 链接
链接分为行内式和参考式

- 行内式链接

	[这是一个行内链接](https://github.com/LeeSniper "这里是标题")

- 参考式链接
	
	这里在有两种参考式链接的例子，[我的github][1]，[MarkDown语法][]

	[1]:https://github.com/LeeSniper "这里是标题"
	
	[MarkDown语法]:http://www.cnblogs.com/rossoneri/p/4446440.html

## 图片

也分为行内式和链接式

- 行内式格式：! + [替代图片的文字，可空] + (路径 title)

- 链接式格式：! + [替代图片的文字，可空] + [id]
                      [id]: 路径 title

## 强调

*用`*`包起来的斜体*

_用`_`包起来的斜体_

**用两个`*`包起来的粗体**

__用两个`_`包起来的粗体__

注意符号两端不能有空格，否则会作为普通文字处理

## 删除线

~~用两个表示删除线~~

## 行内代码

用`反引号`包起来表示行内的代码


## 反斜杠

	\   反斜线
	`   反引号
	*   星号
	_   底线
	{}  花括号
	[]  方括号
	()  括弧
	#   井字号
	+   加号
	-   减号
	.   英文句点
	!   惊叹号
	
## 表格

表头1  | 表头2
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

| 表头1  | 表头2|
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

| 名字 | 描述          |
| ------------- | ----------- |
| Help      | Display the help window.|
| Close     | Closes a window     |

表格中也可以使用普通文本的删除线，斜体等效果

| 名字 | 描述          |
| ------------- | ----------- |
| Help      | ~~Display the~~ help window.|
| Close     | _Closes_ a window     |

表格可以指定对齐方式

| 左对齐 | 居中  | 右对齐 |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |


## github特有的特性

在列表符号后面加上`[]`或者`[x]`代表选中或者未选中情况
