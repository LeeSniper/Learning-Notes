Glide学习笔记

1.添加依赖

	compile 'com.github.bumptech.glide:glide:3.7.0'
	
2.添加网络权限

<uses-permission android:name="android.permission.INTERNET"/>

3.基本用法

Glide.with(context).load(url).into(imageView);



requestManager.load()使用

Glide基本可以load任何可以拿到的媒体资源，如：

loadSD卡资源：

	load("file://"+ Environment.getExternalStorageDirectory().getPath()+"/test.jpg")
loadassets资源：

	load("file:///android_asset/f003.gif")
loadraw资源：

	load("Android.resource://com.frank.glide/raw/raw_1")或load("android.resource://com.frank.glide/raw/"+R.raw.raw_1)
loaddrawable资源：

	load("android.resource://com.frank.glide/drawable/news")或load("android.resource://com.frank.glide/drawable/"+R.drawable.news)
loadContentProvider资源：

	load("content://media/external/images/media/139469")
loadhttp资源：

	load("http://img.my.csdn.net/uploads/201508/05/1438760757_3588.jpg")
loadhttps资源：

	load("https://img.alicdn.com/tps/TB1uyhoMpXXXXcLXVXXXXXXXXXX-476-538.jpg_240x5000q50.jpg_.webp")







1、thumbnail(float sizeMultiplier). 请求给定系数的缩略图。如果缩略图比全尺寸图先加载完，就显示缩略图，否则就不显示。系数sizeMultiplier必须在(0,1)之间，可以递归调用该方法。

2、sizeMultiplier(float sizeMultiplier). 在加载资源之前给Target大小设置系数。

3、diskCacheStrategy(DiskCacheStrategy strategy).设置缓存策略。DiskCacheStrategy.SOURCE：缓存原始数据，DiskCacheStrategy.RESULT：缓存变换(如缩放、裁剪等)后的资源数据，DiskCacheStrategy.NONE：什么都不缓存，DiskCacheStrategy.ALL：缓存SOURC和RESULT。默认采用DiskCacheStrategy.RESULT策略，对于download only操作要使用DiskCacheStrategy.SOURCE。

4、priority(Priority priority). 指定加载的优先级，优先级越高越优先加载，但不保证所有图片都按序加载。枚举Priority.IMMEDIATE，Priority.HIGH，Priority.NORMAL，Priority.LOW。默认为Priority.NORMAL。

５、dontAnimate(). 移除所有的动画。

６、animate(int animationId). 在异步加载资源完成时会执行该动画。

７、animate(ViewPropertyAnimation.Animator animator). 在异步加载资源完成时会执行该动画。

８、placeholder(int resourceId). 设置资源加载过程中的占位Drawable。

９、placeholder(Drawable drawable). 设置资源加载过程中的占位Drawable。

10、fallback(int resourceId). 设置model为空时要显示的Drawable。如果没设置fallback，model为空时将显示error的Drawable，如果error的Drawable也没设置，就显示placeholder的Drawable。

11、fallback(Drawable drawable).设置model为空时显示的Drawable。

12、error(int resourceId).设置load失败时显示的Drawable。

13、error(Drawable drawable).设置load失败时显示的Drawable。

14、listener(RequestListener<? super ModelType, TranscodeType> requestListener). 监听资源加载的请求状态，可以使用两个回调：onResourceReady(R resource, T model, Target<R> target, boolean isFromMemoryCache, boolean isFirstResource)
和onException(Exception e, T model, Target<R> target, boolean isFirstResource)
，但不要每次请求都使用新的监听器，要避免不必要的内存申请，可以使用单例进行统一的异常监听和处理。

15、skipMemoryCache(boolean skip). 设置是否跳过内存缓存，但不保证一定不被缓存（比如请求已经在加载资源且没设置跳过内存缓存，这个资源就会被缓存在内存中）。

16、override(int width, int height). 重新设置Target的宽高值（单位为pixel）。

17、into(Y target).设置资源将被加载到的Target。

18、into(ImageView view). 设置资源将被加载到的ImageView。取消该ImageView之前所有的加载并释放资源。

19、into(int width, int height). 后台线程加载时要加载资源的宽高值（单位为pixel）。

20、preload(int width, int height). 预加载resource到缓存中（单位为pixel）。

21、asBitmap(). 无论资源是不是gif动画，都作为Bitmap对待。如果是gif动画会停在第一帧。

22、asGif().把资源作为GifDrawable对待。如果资源不是gif动画将会失败，会回调.error()
。










4.加载的图片过大时,或者网络不好时,设置占位图(placeholder)

Glide.with(this).load(url).placeholder(R.mipmap.place).into(iv);

5.图片链接地址有误或者网络不行的时候,设置错误图片(error)

Glide.with(this).load(url).placeholder(R.mipmap.place).error(R.mipmap.icon_photo_error).into(iv);

6.Glide默认是包含淡入淡出动画的时间为300ms(毫秒),我们可以修改这个动画的时间(crossFade)

Glide.with(this).load(url).placeholder(R.mipmap.place).error(R.mipmap.icon_photo_error).crossFade(5000).into(iv);

7.取消默认的淡入淡出动画(dontAnimate)

Glide.with(this).load(url).placeholder(R.mipmap.place).error(R.mipmap.icon_photo_error).dontAnimate().into(iv);

8.加载本地图片

配置权限

<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>

//本地文件
    File file = new File(Environment.getExternalStorageDirectory(), "xiayu.png");
    //加载图片
    Glide.with(this).load(file).into(iv);
    
9.简单加载gif图片

Glide.with(this).load(mGifUrl).placeholder(R.mipmap.place).error(R.mipmap.icon_photo_error).into(mIv);

10.把gif当作普通图片加载(asBitmap)，第一帧

Glide.with(this).load(mGifUrl).asBitmap().placeholder(R.mipmap.place).error(R.mipmap.icon_photo_error).into(mIv);

11.检查是否gif(asGif)

如果你希望加载的只是gif,如果不是gif就显示错误图片,那么只用加上asGif方法即可

Glide.with(this).load(mGifUrl).asGif().placeholder(R.mipmap.place).error(R.mipmap.icon_photo_error).into(mIv);

12.加载本地视频第一帧缩略图

mVideoFile = new File(Environment.getExternalStorageDirectory(), "xiayu.mp4");

    Glide.with(this).load(mVideoFile).placeholder(R.mipmap.place).error(R.mipmap.icon_photo_error).into(mIv);
    


Bitmap

直接跟他要bitmap, 可以用在設大圖background
Bitmap theBitmap = Glide.with(context)
        .load(url)
        .asBitmap()
        .into(100, 100). // Width and height
        .get();
        
        
Thumbnail

縮略圖, 0.1f就是原本的十分之一
Glide.with(context)
    .load(url)
    .thumbnail(0.1f)
    .into(imageView)






13.绑定生命周期

同时将Activity/Fragment作为with()参数的好处是：图片加载会和Activity/Fragment的生命周期保持一致，比如在Paused状态暂停加载，在Resumed的时候又自动重新加载。所以我建议传参的时候传递Activity 和 Fragment给Glide，而不是Context。







14.缓存策略

Glide的缓存资源分为两种:

1.原图(SOURCE) :原始图片
2.处理图(RESULT) :经过压缩和变形等处理后的图片

2.内存缓存策略(skipMemoryCache)

Glide默认是会在内存中缓存处理图(RESULT)的.

可以通过调用skipMemoryCache(true)来设置跳过内存缓存

    //跳过内存缓存
    Glide.with(this).load(mUrl).skipMemoryCache(true).into(mIv);
调用skipMemoryCache(false)没有代码上的意义,因为Glide默认就是不跳过内存缓存的,但是显示调用这个方法,可以让别人一目了然的知道你这次请求是会在内存中缓存的,所以还是建议显示调用一下这个方法来表明你的内存缓存策略


3.磁盘缓存策略(diskCacheStrategy)

Glide磁盘缓存策略分为四种,默认的是RESULT(默认值这一点网上很多文章都写错了,但是这一点很重要):

1.ALL:缓存原图(SOURCE)和处理图(RESULT)

2.NONE:什么都不缓存

3.SOURCE:只缓存原图(SOURCE)

4.RESULT:只缓存处理图(RESULT) —默认值



4.组合策略

和其他三级缓存一样,Glide的缓存读取顺序是 内存–>磁盘–>网络

需要注意的是Glide的内存缓存和磁盘缓存的配置相互没有直接影响,所以可以同时进行配置

例:

1.内存不缓存,磁盘缓存缓存所有图片

Glide.with(this).load(mUrl).skipMemoryCache(true).diskCacheStrategy(DiskCacheStrategy.ALL).into(mIv);
2.内存缓存处理图,磁盘缓存原图

Glide.with(this).load(mUrl).skipMemoryCache(false).diskCacheStrategy(DiskCacheStrategy.SOURCE).into(mIv);



5.缓存大小及路径

5.1内存缓存最大空间

Glide的内存缓存其实涉及到比较多的计算,这里就介绍最重要的一个参数,就是内存缓存最大空间

内存缓存最大空间(maxSize)=每个进程可用的最大内存 * 0.4

(低配手机的话是: 每个进程可用的最大内存 * 0.33)

5.2磁盘缓存大小

磁盘缓存大小: 250 * 1024 * 1024(250MB)

/** 250 MB of cache. */
    int DEFAULT_DISK_CACHE_SIZE = 250 * 1024 * 1024;
5.3磁盘缓存目录

磁盘缓存目录: 项目/cache/image_manager_disk_cache

    String DEFAULT_DISK_CACHE_DIR = "image_manager_disk_cache";
    
    
    
6.清除缓存

6.1清除所有缓存

清除所有内存缓存(需要在Ui线程操作)

Glide.get(this).clearMemory();
清除所有磁盘缓存(需要在子线程操作)

Glide.get(MainActivity.this).clearDiskCache();
注:在使用中的资源不会被清除

6.2清除单个缓存

由于Glide可能会缓存一张图片的多个分辨率的图片,并且文件名是被哈希过的,所以并不能很好的删除单个资源的缓存,



通过自定义Modules定制Glide

1.创建一个类实现GlideModule

2.配置清单文件

在AndroidManifest中配置刚刚创建的GlideModule,需要在application节点下添加

	<application>
    ...

    <meta-data
        android:name="com.xiayu.xiayuglidedemo.XiayuGlideModule"
        android:value="GlideModule" />
</application>
其中Android:name就是刚才创建的GlideModule的实现类



	@Override
    public void applyOptions(Context context, GlideBuilder builder) {

        builder.setDiskCache();//自定义磁盘缓存

        builder.setMemoryCache();//自定义内存缓存

        builder.setBitmapPool(); //自定义图片池

        builder.setDiskCacheService();//自定义本地缓存的线程池

        builder.setResizeService();//自定义核心处理的线程池

        builder.setDecodeFormat();//自定义图片质量

    }
    
    
    
    例如：自定义图片质量
    //自定义图片质量
    builder.setDecodeFormat(DecodeFormat.PREFER_ARGB_8888);
    //配置内存缓存大小 10MB
    builder.setMemoryCache(new LruResourceCache(10*1024*1024));
    //配置图片池大小   20MB
    builder.setBitmapPool(new LruBitmapPool(20*1024*1024));
    
    
    但是内存缓存的大小数值其实不应该是随便配置的,Glide的内部的默认值是通过一系列的计算获取的,比如说判断手机是否高配置手机等(有兴趣的可以去看他的源码,或者等待本系列后面的源码分析) 
    这样有个取巧的办法,就是获取Glide默认的设置,然后在这个设置的基础上进行修改
    
    //获取内存计算器
        MemorySizeCalculator calculator = new MemorySizeCalculator(context);
        //获取Glide默认内存缓存大小
        int                  defaultMemoryCacheSize = calculator.getMemoryCacheSize();
        //获取Glide默认图片池大小
        int                  defaultBitmapPoolSize  = calculator.getBitmapPoolSize();
        //将数值修改为之前的1.1倍
        int                  myMemoryCacheSize  = (int) (1.1 * defaultMemoryCacheSize);
        int                  myBitmapPoolSize   = (int) (1.1 * defaultBitmapPoolSize);
        //修改默认值
        builder.setMemoryCache(new LruResourceCache(myMemoryCacheSize));
        builder.setBitmapPool(new LruBitmapPool(myBitmapPoolSize));
        
        
        
3.自定义磁盘缓存

磁盘缓存按照访问权限及路径可以分为两种 
- 私有缓存 (自己本app可以使用,目录在data/data/应用包名 下面) 
- 外部缓存(都可以访问,目录在扩展空间内,如SD卡)

3.1私有缓存

下面这样配置的话,主要是修改缓存大小,缓存路径仍为默认路径(即data/data/应用包名/cache/image_manager_disk_cache)

	public class XiayuGlideModule implements GlideModule {

    	@Override
    	public void applyOptions(Context context, GlideBuilder builder) {
        	//设置磁盘缓存大小
        	int size = 100 * 1024 * 1024;
        	//设置磁盘缓存
        	builder.setDiskCache(new InternalCacheDiskCacheFactory(context, size));
    	}

    	@Override
    	public void registerComponents(Context context, Glide glide) {

    	}
	}
如果需求修改缓存路径的话,需要增加一下参数即可(变为data/data/应用包名/cache/xiayu)

    //设置磁盘缓存大小
    int size = 100 * 1024 * 1024;
    String dir = "xiayu";
    //设置磁盘缓存
    builder.setDiskCache(new InternalCacheDiskCacheFactory(context,dir, size));
3.2外部缓存

下面这样配置的话,缓存会在 SDCard/Android/data/应用包名/cache/image_manager_disk_cache目录下

	public class XiayuGlideModule implements GlideModule {

    	@Override
    	public void applyOptions(Context context, GlideBuilder builder) {
        	//设置磁盘缓存大小
        	int size = 100 * 1024 * 1024;
        	//设置磁盘缓存
        	builder.setDiskCache(new ExternalCacheDiskCacheFactory(context, size));
    	}

    	@Override
    	public void registerComponents(Context context, Glide glide) {

    	}
	}
如果需求修改缓存路径的话,需要增加一下参数即可(变为SDCard/android/data/应用包名/cache/xiayu)

    //设置磁盘缓存大小
    int size = 100 * 1024 * 1024;
    String dir = "xiayu";
    //设置磁盘缓存
    builder.setDiskCache(new ExternalCacheDiskCacheFactory(context,dir, size));
3.3完全自定义路径

上面两种缓存都是把缓存的父目录定死的,能够改变的只是子目录,Glide还提供了一种方式可以完全自定义缓存目录

(需要注意的是这里的路径是配置的绝对路径,所以如果没有指定在sd卡目录下的话是无法直接看到的)

	public class XiayuGlideModule implements GlideModule {

    	@Override
    	public void applyOptions(Context context, GlideBuilder builder) {
        	//设置磁盘缓存大小
        	int size = 100 * 1024 * 1024;
        	String dirFolder = "xia";
        	String dirName = "yu";
        	//设置磁盘缓存
        	builder.setDiskCache(new DiskLruCacheFactory(dirFolder, size));

        	//builder.setDiskCache(new DiskLruCacheFactory(dirFolder, dirName,size));
    	}

    	@Override
    	public void registerComponents(Context context, Glide glide) {

    	}
	}






1.Android图片显示相关知识

这里会讲一下图片显示相关的基础知识,如果不关心的可以直接跳到第二点,不过建议是最好看一下

1.1图片质量分类

安卓图片显示的质量配置主要分为四种:

ARGB_8888 :32位图,带透明度,每个像素占4个字节
ARGB_4444 :16位图,带透明度,每个像素占2个字节
RGB_565 :16位图,不带透明度,每个像素占2个字节
ALPHA_8 :32位图,只有透明度,不带颜色,每个像素占4个字节
(A代表透明度,RGB代表红绿蓝:即颜色)

1.2图片默认质量

Picasso的默认质量是 ARGB_8888 
Glide的默认质量则为 RGB_565

1.3占用内存

加载一张4000 * 2000(一般手机拍摄的都超过这个像素)的图片

Picasso需要占用的内存为: 32MB

4000 * 2000 * 4 / 1024 / 1024 = 30 (MB)

Glide需要占用的内存为: 16MB

4000 * 2000 * 2 / 1024 / 1024 = 15 (MB)

也就是说只要同时加载几张图片,你的应用就会OOM(内存溢出了),最恐怖的是就算你的ImageView的宽高只有10px,同样会占用那么多内存,这就是为什么需要做图片压缩的原因了


3.图片尺寸的压缩或者拉伸(override)

通过调用override,就可以把图片压缩到相应的尺寸来显示了,类似这些被处理过的图片,就是之前文章中提到的RESULT(处理图)

	Glide.with(this)
		.load(mUrl)
		.override(300,300)
		.into(mIv);
注意,这里具体会压缩到什么尺寸还会根据很多条件来计算,所以最终压缩的结果的宽高会比较接近你的传值,但是不一定会完全相同,如果感兴趣的可以期待本系列后面的Glide源码解析中的具体介绍





## 图像变换图片预处理(圆角,高斯模糊等)

1.创建一个类继承BitmapTransformation

2.使用

通过调用transform方法就能展示处理后的图片

	Glide.with(this)
		.load(url)
		.transform(new CornersTransform())
		.into(iv1);

4.使用多个transform

transform方法是不支持多次调用的,如果你调用了两次,那么第二次的会覆盖了第一次的效果

但是他有一个重载的方法可以传入多个对象,这样传入的变形器都能够生效

	Glide.with(this)
		.load(url)
		.transform(new CircleTransform(this),new CornersTransform(this,50))
		.into(iv1);

5.三方库

如果你觉得自己自定义transform比较困难,或者你想学习别人的图片处理方法,可以在试一试github上的这个三方库

Glide Transformations

https://github.com/wasabeef/glide-transformations



## 基本使用

## 缓存


## request
请求接口。为target加载资源的一个请求，主要包括状态判断函数、修改状态的函数

## RequestBuilder
主要方法：

- apply
- clone
- into
- load
- listener
- submit
- thumbnail
- transition


## RequestOptions


## 生命周期管理LifecycleListener

LifecycleListener接口用来监听fragment和activity的生命周期事件，包含三个方法：onStart,onStop和onDestroy，分别对应Fragment和Activity的三种声明周期回调。

## Target

问题：target是什么？有什么功能？扮演什么角色？怎么用？

target是个接口，主要包含以下方法：

- onLoadStarted：加载开始时的生命周期回调
- onResourceReady：加载成功
- onLoadCleared：加载取消而且资源被释放后回调
- onLoadFailed：加载失败
- getSize：
- removeCallback
- getRequest：
- setRequest

同时，target接口继承了LifecycleListener接口。所以从target接口的功能上来看，它是glide再一次加载过程中处理声明周期事件。

典型的生命周期是onLoadStarted -> onResourceReady 或者 onLoadFailed -> onLoadCleared，但是并不保证一定如此。onLoadStarted可能会因为资源已经在内存中或者因为对象为空加载失败而不调用。onLoadCleared可能因为target从未被清理，而一直没有调用。






## 参考资料

[Glide-图片的剪裁(ScaleType)](http://blog.csdn.net/yulyu/article/details/55261439)

[Glide-源码详解](http://blog.csdn.net/yulyu/article/details/60331803)

[Glide封装个工具类直接使用](http://www.jianshu.com/p/92070f357068)整理的很好

[Glide详解](http://www.voidcn.com/article/p-zipclpcp-bmd.html)讲解很详细，而且提到很多高级用法，值得研究

[Glide使用详解（一）](http://blog.csdn.net/shangmingchao/article/details/51125554)主要是后面几篇文章很不错，值得学习

[Glide Wiki](https://github.com/bumptech/glide/wiki)

[Glide - 开始！](https://mrfu.me/2016/02/27/Glide_Getting_Started/)另一个系列，整理的也不错

[Google推荐的图片加载库Glide介绍](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2015/0327/2650.html)glide与picaso的对比
