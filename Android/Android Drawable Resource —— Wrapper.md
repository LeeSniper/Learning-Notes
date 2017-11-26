# Android Drawable Resource —— Wrapper


## <bitmap\>
安卓中支持以下三种格式的位图文件：.png、.jpg、.gif，首选的是.png类型。我们可以将图片文件根据尺寸保存在不同分辨率的res/drawable/或者res/mipmap/文件夹下，用文件名作为资源ID来引用这些图片资源。那么为什么还要定义<bitmap\>标签呢？
### 语法

	<?xml version="1.0" encoding="utf-8"?>
	<bitmap
	    xmlns:android="http://schemas.android.com/apk/res/android"
	    android:src="@[package:]drawable/drawable_resource"
	    android:antialias=["true" | "false"]
	    android:dither=["true" | "false"]
	    android:filter=["true" | "false"]
	    android:gravity=["top" | "bottom" | "left" | "right" | "center_vertical" |
	                      "fill_vertical" | "center_horizontal" | "fill_horizontal" |
	                      "center" | "fill" | "clip_vertical" | "clip_horizontal"]
	    android:mipMap=["true" | "false"]
	    android:tileMode=["disabled" | "clamp" | "repeat" | "mirror"] />

### 属性

- xmlns:android：定义 XML 命名空间，必须是 "http://schemas.android.com/apk/res/android"。仅当 <bitmap> 是根元素时才需要，当 <bitmap> 嵌套在 <item> 内时不需要。
- android:src：必备。引用的图片资源
- android:antialias：启用或者停用抗锯齿
- android:dither：当位图的像素配置与屏幕不同时（例如：ARGB 8888 位图和 RGB 565 屏幕），启用或停用位图抖动。
- android:filter：启用或停用位图过滤。当位图收缩或拉伸以使其外观平滑时使用过滤。
- android:gravity
- android:mipMap：启用或停用 mipmap 提示。默认值为 false。
- android:tileMode：定义平铺模式，当启用平铺模式的时候，位图会重复，gravity属性将被忽略

	- disabled：默认值，不平铺位图
	- clamp：当着色器绘制范围超出其原边界时复制边缘颜色
	- repeat：水平和垂直重复着色器的图像。
	- mirror：水平和垂直重复着色器的图像，交替镜像图像以使相邻图像始终相接。

## <nine-patch\>
### 语法

	<?xml version="1.0" encoding="utf-8"?>
	<nine-patch
    	xmlns:android="http://schemas.android.com/apk/res/android"
    	android:src="@[package:]drawable/drawable_resource"
    	android:dither=["true" | "false"] />

### 属性

- xmlns:android：定义 XML 命名空间，其必须是 "http://schemas.android.com/apk/res/android"。
- android:src：必备。引用九宫格文件。
- android:dither：当位图的像素配置与屏幕不同时（例如：ARGB 8888 位图和 RGB 565 屏幕），启用或停用位图抖动。

clip

scale

inset

rotate