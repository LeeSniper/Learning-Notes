安卓学习笔记——图片资源

bitmap 文件

.9图

layer_list

state_list

level_list

shape



根节点

animated-rotate
animated-selector
animated-vector
animation-list

## bitmap
#### 1、属性

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

- xmlns:android
- android:src
- android:antialias
- android:dither
- android:filter
- android:gravity
- android:mipMap
- android:tileMode

#### 2、子节点

clip

color

inset

## layer-list
#### 1、属性

#### 2、子节点


## level-list
#### 1、属性

#### 2、子节点


## nine-patch
#### 1、属性

#### 2、子节点


ripple

rotate

scale

selector

## <shape\>
xml定义的一般形状，<shape\>标签必须作为根节点。

#### 1、属性
##### xmlns:android
必备属性。定义XML命名空间，必须是"http://schemas.android.com/apk/res/android"。

##### android:shape
- 

#### 2、子节点

transition

vector





子节点
item