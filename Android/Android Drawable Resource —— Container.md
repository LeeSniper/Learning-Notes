# Android Drawable Resource —— Container


## layer-list

layer表示图层，layer-list就是指图层列表，每一个Item元素代表一个图层，按照列表的顺序依次绘制图层，最后一个图层在最上面。

### 1、语法

	<?xml version="1.0" encoding="utf-8"?>
	<layer-list
    	xmlns:android="http://schemas.android.com/apk/res/android" >
    	<item
        	android:drawable="@[package:]drawable/drawable_resource"
        	android:id="@[+][package:]id/resource_name"
        	android:top="dimension"
        	android:right="dimension"
        	android:bottom="dimension"
        	android:left="dimension" />
	</layer-list>

### 2、包含的元素及相应的属性

#### <layer-list\>

这个标签必须是根元素，可以包含一个或者多个<item>元素。

- xmlns:android：必备。定义 XML 命名空间，必须是 "http://schemas.android.com/apk/res/android"。

#### <item\>
- android:drawable：必备。引用可绘制对象资源。
- android:id：
- android:top：整型。顶部偏移（像素）。
- android:right：整型。右边偏移（像素）。
- android:bottom：整型。底部偏移（像素）。
- android:left：整型。左边偏移（像素）。

定义要放在




## selector

### 语法

	<?xml version="1.0" encoding="utf-8"?>
	<selector xmlns:android="http://schemas.android.com/apk/res/android"
    	android:constantSize=["true" | "false"]
    	android:dither=["true" | "false"]
    	android:variablePadding=["true" | "false"] >
    	<item
        	android:drawable="@[package:]drawable/drawable_resource"
        	android:state_pressed=["true" | "false"]
        	android:state_focused=["true" | "false"]
        	android:state_hovered=["true" | "false"]
        	android:state_selected=["true" | "false"]
        	android:state_checkable=["true" | "false"]
        	android:state_checked=["true" | "false"]
        	android:state_enabled=["true" | "false"]
        	android:state_activated=["true" | "false"]
        	android:state_window_focused=["true" | "false"] />
	</selector>

### 包含的元素及相应的属性

#### <selector\>



#### <item\>





## level-list

### 语法

	<?xml version="1.0" encoding="utf-8"?>
	<level-list xmlns:android="http://schemas.android.com/apk/res/android" >
    	<item
        	android:drawable="@drawable/drawable_resource"
        	android:maxLevel="integer"
        	android:minLevel="integer" />
	</level-list>

#### 1、属性

#### 2、子节点


## transition
