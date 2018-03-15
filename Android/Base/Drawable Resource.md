安卓学习笔记——图片资源

## <shape\>
xml定义的通用形状，<shape\>标签必须作为根节点。

### 语法
	
	<?xml version="1.0" encoding="utf-8"?>
	<shape
    	xmlns:android="http://schemas.android.com/apk/res/android"
    	android:shape=["rectangle" | "oval" | "line" | "ring"] >
    	<corners
       		android:radius="integer"
        	android:topLeftRadius="integer"
        	android:topRightRadius="integer"
        	android:bottomLeftRadius="integer"
        	android:bottomRightRadius="integer" />
    	<gradient
        	android:angle="integer"
        	android:centerX="float"
        	android:centerY="float"
        	android:centerColor="integer"
        	android:endColor="color"
        	android:gradientRadius="integer"
        	android:startColor="color"
        	android:type=["linear" | "radial" | "sweep"]
        	android:useLevel=["true" | "false"] />
    	<padding
        	android:left="integer"
        	android:top="integer"
        	android:right="integer"
        	android:bottom="integer" />
    	<size
        	android:width="integer"
        	android:height="integer" />
    	<solid
        	android:color="color" />
    	<stroke
        	android:width="integer"
        	android:color="color"
        	android:dashWidth="integer"
        	android:dashGap="integer" />
	</shape>

### 包含的标签元素以及相应的属性

#### 1、shape

必须作为根元素

- xmlns:android：必备属性。定义XML命名空间，必须是"http://schemas.android.com/apk/res/android"。

- android:shape：定义形状的类型，有以下四种类型：

	- rectangle：矩形，也是默认的形状
	- oval：椭圆形
	- line：
	- ring：环形

- android:innerRadius（只对环形有效）

定义环形内部的半径

- android:innerRadiusRatio（只对环形有效）

- android:thickness（只对环形有效）

- android:thicknessRatio（只对环形有效）

- android:useLevel（只对环形有效）

#### 2、size
定义形状的大小，当作为背景需要填充到view里的时候，会按照size定义的比例进行等比例缩放。ImageView中可以通过将 android:scaleType 设置为"center"来显示XML文件里设置的大小。

- android:height：定义形状的高度
- android:width：定义形状的宽度

#### 3、solid
定义形状的填充色

- android:color：设置颜色


#### 4、corners
设置形状的圆角，只对矩形有用。

- android:radius：所有圆角的半径，对于特定的角如果定义了具体的数值，会被覆盖。
- android:topLeftRadius：左上角的半径
- android:topRightRadius：右上角的半径
- android:bottomLeftRadius：左下角的半径
- android:bottomRightRadius：右下角的半径


#### 5、padding
设置内边距，但是这个内边距什么情况下生效呢？我在shape里面设置了

- android:left
- android:top
- android:right
- android:bottom

#### 6、gradient
定义形状的渐变颜色

- android:type：渐变的类型
	- linear：线性渐变，默认
	- radial：径向渐变，起始颜色为中心的颜色
	- sweep：流线型渐变

- android:startColor：渐变起始颜色
- android:endColor：渐变结束的颜色
- android:centerColor：起始颜色与结束颜色中间的颜色
- android:angle：渐变的角度。只对线性渐变有效，默认值为0，也就是从左到右渐变，90表示从下到上，而且必须是45的倍数。
- android:centerX：渐变中心相对于X轴的位置，取值范围是0到1.0
- android:centerY：渐变中心相对于y轴的位置，取值范围是0到1.0
- android:gradientRadius：渐变半径，只对于径向渐变类型有用
- android:useLevel

#### 7、stroke
定义形状的边框

- android:width：边框的线宽
- android:color：边框的颜色

如果想实现虚线边框效果，必须同时定义以下两个属性：

- android:dashGap：虚线之间的间隔
- android:dashWidth：虚线的宽度






### 参考资料
[Android API Reference](https://developer.android.com/guide/topics/resources/drawable-resource.html#Shape)




