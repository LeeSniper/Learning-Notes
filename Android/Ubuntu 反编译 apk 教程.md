# Ubuntu 反编译 apk 教程


## 工具

apktool, [官方下载及安装教程](https://ibotpeaches.github.io/Apktool/install/)
(下载的文件复制到usr/local/bin 可以通过命令：sudo cp 文件名 /usr/local/bin)

dex2jar，[GitHub地址](https://github.com/pxb1988/dex2jar) [zip文件下载地址](https://sourceforge.net/projects/dex2jar/files/)



## 步骤

1、（非常不实用的方式）将.apk格式重命名为 .zip 格式，然后用 unzip 命令解压。

2、解压资源文件 将 apktool apktool.jar 还有需要反编译的 apk 文件放到同一个目录下，通过命令行  apktool d apk文件名  或者  ./apktool d apk文件名  进行解压。

3、反编译代码