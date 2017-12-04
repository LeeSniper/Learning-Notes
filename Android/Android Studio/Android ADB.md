# Android ADB


## ADB 简介

一种命令行工具，允许开发工具（电脑）与设备（模拟器或者真机）之间进行通讯。由三部分组成：

- 客户端：发送命令。在计算机上运行，通过adb命令从命令行终端发送命令。
- 后台程序：在设备上运行命令。在设备上作为后台程序运行。
- 服务器：管理客户端和后台程序之间的通信。在计算机上作为后台程序运行。


## ADB 工作方式

启动一个 adb 客户端时，此客户端首先检查是否有已运行的 adb 服务器进程。如果没有，它将启动服务器进程。当服务器启动时，它与本地 TCP 端口 5037 绑定，并侦听从 adb 客户端发送的命令—所有 adb 客户端均使用端口 5037 与 adb 服务器通信。

然后，服务器设置与所有运行的模拟器/设备实例的连接。它通过扫描 5555 到 5585 之间（模拟器/设备使用的范围）的奇数号端口查找模拟器/设备实例。服务器一旦发现 adb 后台程序，它将设置与该端口的连接。请注意，每个模拟器/设备实例将获取一对按顺序排列的端口 — 用于控制台连接的偶数号端口和用于 adb 连接的奇数号端口。例如：

模拟器 1，控制台：5554
模拟器 1，adb：5555
模拟器 2，控制台：5556
模拟器 2，adb：5557
以此类推...

如上所示，在端口 5555 与 adb 连接的模拟器实例与侦听端口 5554 的控制台的实例相同。

当服务器已设置与所有模拟器实例的连接后，您可以使用 adb 命令访问这些实例。由于服务器管理与模拟器/设备实例的连接，并处理来自多个 adb 客户端的命令，因此，您可以从任意客户端（或从某个脚本）控制任意模拟器/设备实例。

## ADB 连接

可以通过USB连接，也可以通过WLAN连接
[这里](https://developer.android.com/studio/command-line/adb.html#wireless)有提通过WLAN连接adb该如何设置。

## 常用 ADB 命令

- 查看计算机连接的设备信息（设备序列号和连接状态）

		adb devices
		
- 将命令发送至特定设备

		adb -s serial_number command
	
	如果连接多个设备，而不指定目标设备，adb会报错。如果有多个设备但是只有一个模拟器，可以用-e选项将命令发送给这个模拟器。如果有多个设备但是只有一个是真机，其他都是模拟器，则可以用-d选项将命令发送给这台真机。
		
- 安装应用

		adb install 计算机上的apk文件路径
		
- 从模拟器或设备复制文件或目录（及其子目录）

		adb pull remote local
		
- 将文件文件或目录（及其子目录）复制到模拟器或设备

		adb push local remote
		
	local 和 remote 指的是开发计算机（本地）和模拟器/设备实例（远程）上目标文件/目录的路径
		
- 检查并启动 adb 服务器

		adb start-server
			
- 停止 adb 服务器

		adb kill-server
		
- 输出支持的 adb 命令的列表

		adb help
		
- 输出 adb 版本号

		adb version
		
- 输出日志数据

		adb logcat [option] [filter-specs]
		
- 将 dumpsys、dumpstate 和 logcat 数据输出到屏幕，以用于报告错误

		adb bugreport
		
- 输出 adb 实例序列号

		adb get-serialno
		
- 输出模拟器/设备实例的 adb 状态

		adb get-state
		
- 阻止执行，直至设备处于在线状态

		adb wait-for-device
		
## 常用 ADB SHELL 命令

可以不进入模拟器或者设备上的adb远程shell发送命令，也可以进入远程shell发送命令。

不进入：

	adb [-d|-e|-s serial_number] shell shell_command

进入远程shell：

	adb [-d|-e|-s serial_number] shell
	
退出远程shell可以输入exit或者按Control + D。以下的常用命令为了方便起见，以进入远程shell为例。

#### 调用Activity Manager (am)









adb的全称为Android Debug Bridge 调试桥，是连接Android手机与PC端的桥梁，通过adb可以管理、操作模拟器和设备，如安装软件、系统升级、运行shell命令等。

文件操作

	//android中，sdcard代表内置存储，不同系统中tf卡的设备名可能不同，使用查看adb shell ls mnt查看所有存储设备名。
	adb remount  // 将system分区重新挂载为可读写分区
	adb push <local> <remote> // 从本地复制文件到设备
	adb pull <remote>  <local> // 从设备复制文件到本地
	adb shell ls // 列出目录下的文件和文件夹，等同于dos中的dir命令
	adb shell cd <folder> // 进入文件夹，等同于dos中的cd 命令
	adb shell rename path/oldfilename path/newfilename // 重命名文件
	adb shell rm /system/avi.apk  // 删除system/avi.apk
	adb shell rm -r <folder> // 删除文件夹及其下面所有文件
	adb shell mv path/file newpath/file // 移动文件
	adb shell chmod 777 /system/fonts/DroidSansFallback.ttf // 设置文件权限
	adb shell mkdir path/foldelname // 新建文件夹
	adb shell cat <file> // 查看文件内容
	
	
管理设备APP

	aapt d badging <apkfile> // 获取apk的packagename 和 classname
	------------------安装----------------------------------------------
	adb install <apkfile>  // 安装apk
	adb install -r <apkfile> // 保留数据和缓存文件，重新安装apk，
	adb install -s <apkfile>  // 安装apk到sd卡
	------------------卸载----------------------------------------------
	adb uninstall <package>  // 卸载app
	adb uninstall -k <package>  // 卸载app但保留数据和缓存文件
	------------------启动app-------------------------------------------
	adb shell am start -n <package_name>/.<activity_class_name> // 启动应用
	------------------查看内存占用----------------------------------------
	adb shell top  // 查看设备cpu和内存占用情况
	adb shell top -m 6 // 查看占用内存前6的app
	adb shell top -n 1 // 刷新一次内存信息，然后返回
	adb shell procrank // 查询各进程内存使用情况
	adb shell kill [pid] // 杀死一个进程
	adb shell ps // 查看进程列表
	adb shell ps -x [PID] // 查看指定进程状态
	adb shell service list // 查看后台services信息
	adb shell cat /proc/meminfo // 查看当前内存占用
	adb shell cat /proc/iomem // 查看IO内存分区
	
	
获取设备硬件信息

	adb shell  cat /sys/class/net/wlan0/address  // 获取mac地址
	adb shell cat /proc/cpuinfo  // 获取cpu序列号
	
	
adb相关

	adb kill-server // 终止adb服务进程
	adb start-server // 重启adb服务进程
	adb root // 已root权限重启adb服务
	adb wait-for-device // 在模拟器/设备连接之前把命令转载在adb的命令器中
	
	
管理设备

	adb devices  // 显示连接到计算机的设备
	adb get-serialno // 获取设备的ID和序列号serialNumber
	------------------重启----------------------------------------------
	adb reboot  // 重启设备
	adb reboot bootloader  // 重启到bootloader，即刷机模式
	adb reboot recovery  // 重启到recovery，即恢复模式
	------------------发送命令到设备--------------------------------------
	adb [-d|-e|-s <serialNumber>] <command>
	-d 发送命令给usb连接的设备
	-e 发送命令到模拟器设备
	-s <serialNumber> 发送命令到指定设备
	
	
ADB很强大，记住一些ADB命令有助于提高工作效率。

获取序列号：

 adb get-serialno
查看连接计算机的设备：

 adb devices
重启机器：

 adb reboot
重启到bootloader，即刷机模式：

 adb reboot bootloader
重启到recovery，即恢复模式：

 adb reboot recovery
查看log：

 adb logcat
终止adb服务进程：

 adb kill-server
重启adb服务进程：

 adb start-server
获取机器MAC地址：

 adb shell  cat /sys/class/net/wlan0/address
获取CPU序列号：

adb shell cat /proc/cpuinfo
安装APK：

adb install <apkfile> //比如：adb install baidu.apk
保留数据和缓存文件，重新安装apk：

adb install -r <apkfile> //比如：adb install -r baidu.apk
安装apk到sd卡：

adb install -s <apkfile> // 比如：adb install -s baidu.apk
卸载APK：

adb uninstall <package> //比如：adb uninstall com.baidu.search
卸载app但保留数据和缓存文件：

adb uninstall -k <package> //比如：adb uninstall -k com.baidu.search
启动应用：

adb shell am start -n <package_name>/.<activity_class_name>
查看设备cpu和内存占用情况：

adb shell top
查看占用内存前6的app：

adb shell top -m 6
刷新一次内存信息，然后返回：

adb shell top -n 1
查询各进程内存使用情况：

adb shell procrank
杀死一个进程：

adb shell kill [pid]
查看进程列表：

adb shell ps
查看指定进程状态：

adb shell ps -x [PID]
查看后台services信息：

adb shell service list
查看当前内存占用：

adb shell cat /proc/meminfo
查看IO内存分区：

adb shell cat /proc/iomem
将system分区重新挂载为可读写分区：

adb remount
从本地复制文件到设备：

adb push <local> <remote>
从设备复制文件到本地：

adb pull <remote>  <local>
列出目录下的文件和文件夹，等同于dos中的dir命令：

adb shell ls
进入文件夹，等同于dos中的cd 命令：

adb shell cd <folder>
重命名文件：

adb shell rename path/oldfilename path/newfilename
删除system/avi.apk：

adb shell rm /system/avi.apk
删除文件夹及其下面所有文件：

adb shell rm -r <folder>
移动文件：

adb shell mv path/file newpath/file
设置文件权限：

adb shell chmod 777 /system/fonts/DroidSansFallback.ttf
新建文件夹：

adb shell mkdir path/foldelname
查看文件内容：

adb shell cat <file>
查看wifi密码：

adb shell cat /data/misc/wifi/*.conf
清除log缓存：

adb logcat -c
查看bug报告：

adb bugreport
获取设备名称：

adb shell cat /system/build.prop
查看ADB帮助：

adb help
跑monkey：

adb shell monkey -v -p your.package.name 500