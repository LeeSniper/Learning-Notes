# Systrace 的使用

## 抓取 systrace
两种方式：

##### 1、使用 systrace.py 工具
`systrace.py` 脚本位于 Android SDK 目录 `/skd/platform-tools/systrace` 中，所以要先打开该目录。

命令行是

	python systrace.py [options] [category1] [category2] ... [categoryN]

示例如下：

	cd android-sdk/platform-tools/systrace
	python systrace.py --time=10 -o mynewtrace.html sched gfx view wm

###### 1.1 options 可取值

|options    | 说明 |
|---------- | ------|
| -o <File> | 输出的目标文件 |
| -t N, --time=N | 执行时间 N 秒，默认为 5 秒 
| -b N, --buf-size=N | 设置 buffer 的大小，单位为 kB，用于限制 trace 文件的总大小，默认无上限
| -a <APP_NAME>, --app=<APP_NAME> | 追踪的应用包名，用逗号分隔
| -e <DEVICE_SERIAL>, --serial=<DEVICE_SERIAL> | 指定设备
| -k <KFUNCS>, --ktrace=<KFUNCS> | 跟踪 kernel 函数，用逗号分隔
| --from-file=<FROM_FILE> | 从文件中创建互动的 systrace
| -l, --list-categories | 列举所有可用的 category tag
| -h, --help | 显示帮助信息

###### 1.2 category 可取值

|category   | 说明 |
|---------- | ------|
| gfx 			| Graphics 对分析卡顿非常重要
| input			| Input
| view			| View System 对分析卡顿很有帮助
| webview		| WebView
| wm			| Window Manager
| am			| Activity Manager 对分析 Activity 启动过程比较有用
| sm			| Sync Manager
| audio			| Audio
| video			| Video
| camera		| Camera
| hal			| Hardware Modules			
| res			| Resource Loading
| dalvik		| Dalvik VM
| rs			| RenderScript
| bionic		| Bionic C Library
| power			| Power Management
| pm 			| Package Manager
| ss 			| System Server
| database		| Database
| network		| Network
| adb			| ADB
| vibrator		| Vibrator
| aidl			| AIDL Calls
| sched			| CPU Scheduling CPU 调度信息，非常重要
| irq			| IRQ Events
| freq			| CPU Frequency
| idle			| CPU Idle
| disk			| Disk I/O
| sync			| Synchronization
| workq			| Kernel Workqueues
| memreclaim
| regulators

这么多 category 该怎么用呢？什么情况下需要用什么 category 呢？
- CPU 信息，必须带上
		freq sched idle
- 测试 UI 流畅性和卡顿问题
		gfx input view
- 测试 App 启动或者进入某个界面的速度
		gfx input view am wm res
- 怀疑有 GC 或者 IO 导致卡顿
		gfx input view dalvik disk
- power 相关问题，亮灭屏慢等
		gfx input view res am wm power

##### 2、使用 Device Monitor (DDMS)

Tools ——> Android ——> Android Device Monitor

点击工具栏上的 Capture System Wide Trace 功能，在弹窗里面进行配置：

- Destination File：设置输出文件路径
- Trace duration：设置抓取的时间，单位为秒，通常设为 5 秒
- Trace Buffer Size：设置存储的 systrace 的文件大小，单位是 kB，建议 20480。
- Enable Application Traces From：选择追踪的应用包名
- Commonly Used Tags
- Advanced Options

## 自定义 systrace
##### 3.1 app 层

	import android.os.Trace;
	Trace.beginSection(String sectionName)
	Trace.EndSection()

通过上面代码添加自定义的 systrace 信息，然后通过 `python systrace.py --app=sectionName` 指定 apk，或者通过 ddms 选择指定的 apk，抓取 systrace 分析。这里默认的 traceTag 为 TRACE_TAG_APP

##### 3.2 Java framework 层

	import android.os.Trace;
	Trace.traceBegin(long traceTag, String methodName)
	Trace.traceEnd(long traceTag)

在代码中必须成对出现，一般将traceEnd放入到finally语句块，另外，必须在同一个线程。

##### 3.3 Native framework 层
在函数开头声明定义

	#include<utils/Trace.h>
	ATRACE_CALL();

## 分析 systrace

##### 打开 trace.html 文件

1、右键选择使用 Chrome 打开

2、在 Chrome 中加载，遇到打不开或者信息丢失的情况可以使用这种方法
- 启动 Chrome
- 在地址栏输入 `chrome://tracing/`
- 点击 load，选择需要加载的 systrace 文件

##### 快捷方式

| 操作按键 | 作用 |
|----------|------|
| w | 放大，[+shift]速度更快
| s | 缩小，[+shift]速度更快
| a | 左移，[+shift]速度更快
| d | 右移，[+shift]速度更快
| f | 放大当前选中的区域
| m | 标记当前选中的区域，显示选中区域的耗时
| v | 高亮 VSync
| 0 | 恢复到初始状态

## Systrace 与 TraceView 的比较

与TraceView不同的是，systrace需要PC端配合手机端使用；然后systrace也没有办法在代码里面自由滴控制trace的开始和结束。TraceView 运行时开销大，systrace 无法分析非 debug 的 app。
systrace 也有它自身的局限性，其无法收集到 App 进程内的代码执行信息。为了获取更多的详细信息，如 App 运行时正在执行的方法、App 使用的 CPU 资源等，使用 Android Studio 内置的 CPU profiler，或生成的 trace 日志，然后使用 Traceview 查看。





## 分析非 debug 的 App
	Class<?> trace = Class.forName("android.os.Trace");
	Method setAppTracingAllowed = trace.getDeclaredMethod("setAppTracingAllowed", boolean.class);
	setAppTracingAllowed.invoke(null, true);

把这段代码放在 Application 的 `attachBaseContext` 中，这样就可以手动开启App自定义 Label 的 Trace 功能，在非 debuggable 的版本中也适用！
