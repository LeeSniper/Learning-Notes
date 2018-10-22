# ubuntu 环境下手机快速拉取 apk 文件

## 确定包名

前台运行该应用，通过命令行

	adb shell dumpsys activity activities | sed -En -e '/Running activities/,/Run #0/p'
    
查看任务栈信息，确定包名。例如，通过命令行查看到 NovaLauncher 的包名是 com.teslacoilsw.launcher

## 通过包名找到 APK 位置

命令行

	adb shell pm list packages -f | grep 需要过滤的包名 
    
-f 是文件路径的意思，后面过滤的包名字段选取包名中能够明确区分的字段，比如 NovaLauncher 的例子里就是 teslacoilsw

输出结果是：

	package:/data/app/com.teslacoilsw.launcher-vt4iSBKnsZ9vK7f4qR_1yg==/base.apk=com.teslacoilsw.launcher
    
## 得到 apk 路径之后，拉取到本地，并修改名称

命令行

	adb pull /data/app/com.teslacoilsw.launcher-vt4iSBKnsZ9vK7f4qR_1yg==/base.apk nova.apk
    
前面是手机里的 apk 文件路径，后面是希望保存到电脑里的路径和名称。