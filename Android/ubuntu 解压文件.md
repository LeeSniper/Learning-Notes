# ubuntu 解压文件

#### 解压 tar.gz 文件

	tar -zxvf xxx.tar.gz
    
#### 解压 tar.bz2 文件

	tar -jxvf xxx.tar.bz2
    
    
    
.tar 
解包：tar xvf FileName.tar
打包：tar cvf FileName.tar DirName
（注：tar是打包，不是压缩！）
———————————————
.gz
解压1：gunzip FileName.gz
解压2：gzip -d FileName.gz
压缩：gzip FileName

.tar.gz 和 .tgz
解压：tar zxvf FileName.tar.gz
压缩：tar zcvf FileName.tar.gz DirName
———————————————
.bz2
解压1：bzip2 -d FileName.bz2
解压2：bunzip2 FileName.bz2
压缩： bzip2 -z FileName

.tar.bz2
解压：tar jxvf FileName.tar.bz2
压缩：tar jcvf FileName.tar.bz2 DirName
———————————————
.bz
解压1：bzip2 -d FileName.bz
解压2：bunzip2 FileName.bz
压缩：未知

.tar.bz
解压：tar jxvf FileName.tar.bz
压缩：未知
———————————————
.Z
解压：uncompress FileName.Z
压缩：compress FileName
.tar.Z

解压：tar Zxvf FileName.tar.Z
压缩：tar Zcvf FileName.tar.Z DirName
———————————————
.zip
解压：unzip FileName.zip
压缩：zip FileName.zip DirName
———————————————
.rar
解压：rar x FileName.rar
压缩：rar a FileName.rar DirName
———————————————
.lha
解压：lha -e FileName.lha
压缩：lha -a FileName.lha FileName
———————————————
.rpm
解包：rpm2cpio FileName.rpm | cpio -div
———————————————
.deb
解包：ar p FileName.deb data.tar.gz | tar zxf -
———————————————
.tar .tgz .tar.gz .tar.Z .tar.bz .tar.bz2 .zip .cpio .rpm .deb .slp .arj .rar .ace .lha .lzh .lzx .lzs .arc .sda .sfx .lnx .zoo .cab .kar .cpt .pit .sit .sea
解压：sEx x FileName.*
压缩：sEx a FileName.* FileName

sEx只是调用相关程序，本身并无压缩、解压功能，请注意！

gzip 命令 
减少文件大小有两个明显的好处，一是可以减少存储空间，二是通过网络传输文件时，可以减少传输的时间。gzip 是在 Linux 系统中经常使用的一个对文件进行压缩和解压缩的命令，既方便又好用。

语法：gzip [选项] 压缩（解压缩）的文件名该命令的各选项含义如下：

-c 将输出写到标准输出上，并保留原有文件。-d 将压缩文件解压。-l 对每个压缩文件，显示下列字段：     压缩文件的大小；未压缩文件的大小；压缩比；未压缩文件的名字-r 递归式地查找指定目录并压缩其中的所有文件或者是解压缩。-t 测试，检查压缩文件是否完整。-v 对每一个压缩和解压的文件，显示文件名和压缩比。-num 用指定的数字 num 调整压缩的速度，-1 或 --fast 表示最快压缩方法（低压缩比），-9 或--best表示最慢压缩方法（高压缩比）。系统缺省值为 6。指令实例：

gzip *% 把当前目录下的每个文件压缩成 .gz 文件。gzip -dv *% 把当前目录下每个压缩的文件解压，并列出详细的信息。gzip -l *% 详细显示例1中每个压缩的文件的信息，并不解压。gzip usr.tar% 压缩 tar 备份文件 usr.tar，此时压缩文件的扩展名为.tar.gz。




.xz

  解包：tar xvf FileName.tar.xz
  打包：tar cvf FileName.tar DirName
.tar

 解包：tar xvf FileName.tar
 打包：tar cvf FileName.tar DirName
（注：tar是打包，不是压缩！）
.gz

　　解压1：gunzip FileName.gz
　　解压2：gzip -d FileName.gz
　　压缩：gzip FileName
.tar.gz 和 .tgz

　　解压：tar zxvf FileName.tar.gz
　　压缩：tar zcvf FileName.tar.gz DirName
.bz2

　　解压1：bzip2 -d FileName.bz2
　　解压2：bunzip2 FileName.bz2
　　压缩： bzip2 -z FileName
.tar.bz2

　　解压：tar jxvf FileName.tar.bz2        或tar --bzip xvf FileName.tar.bz2
　　压缩：tar jcvf FileName.tar.bz2 DirName
.bz

　　解压1：bzip2 -d FileName.bz
　　解压2：bunzip2 FileName.bz
　　压缩：未知
.tar.bz

  解压：tar jxvf FileName.tar.bz
  压缩：未知
.Z

　解压：uncompress FileName.Z
　压缩：compress FileName
.tar.Z

　　解压：tar Zxvf FileName.tar.Z
　　压缩：tar Zcvf FileName.tar.Z DirName
.zip

　　解压：unzip FileName.zip
　　压缩：zip FileName.zip DirName
　　压缩一个目录使用 -r 参数，-r 递归。例： $ zip -r FileName.zip DirName
.rar

　　解压：rar x FileName.rar
　　压缩：rar a FileName.rar DirName
　　
　　rar请到：http://www.rarsoft.com/download.htm 下载！
　　解压后请将rar_static拷贝到/usr/bin目录（其他由$PATH环境变量指定的目录也可以）：
　　[root@www2 tmp]# cp rar_static /usr/bin/rar
.lha

　　解压：lha -e FileName.lha
　　压缩：lha -a FileName.lha FileName
　　
　　lha请到：http://www.infor.kanazawa-it.ac.jp/~ishii/lhaunix/下载！
　　>解压后请将lha拷贝到/usr/bin目录（其他由$PATH环境变量指定的目录也可以）：
　　[root@www2 tmp]# cp lha /usr/bin/
.rpm

　　解包：rpm2cpio FileName.rpm | cpio -div
.deb

　　解包：ar p FileName.deb data.tar.gz | tar zxf -
.tar .tgz .tar.gz .tar.Z .tar.bz .tar.bz2 .zip .cpio .rpm .deb .slp .arj .rar .ace .lha .lzh .lzx .lzs .arc .sda .sfx .lnx .zoo .cab .kar .cpt .pit .sit .sea

　　解压：sEx x FileName.*
　　压缩：sEx a FileName.* FileName
　　
　　sEx只是调用相关程序，本身并无压缩、解压功能，请注意！
　　sEx请到： http://sourceforge.net/projects/sex下载！
　　解压后请将sEx拷贝到/usr/bin目录（其他由$PATH环境变量指定的目录也可以）：
　　[root@www2 tmp]# cp sEx /usr/bin/
Linux下常见文件解压方法及命令

以.a为扩展名的文件:
tar xv file.a
以.z为扩展名的文件:
uncompress file.Z
以.gz为扩展名的文件:
gunzip file.gz
以.bz2为扩展名的文件:
bunzip2 file.bz2
以.tar.Z为扩展名的文件:
tar xvZf file.tar.Z
或 compress -dc file.tar.Z | tar xvf
以.tar.gz/.tgz为扩展名的文件:
tar xvzf file.tar.gz
或 gzip -dc file.tar.gz | tar xvf -
以.tar.bz2为扩展名的文件:
tar xvIf file.tar.bz2
或 bzip2 -dc file.tar.bz2 | xvf -
8.以.cpio.gz/.cgz为扩展名的文件:

gzip -dc file.cgz | cpio -div
9.以.cpio/cpio为扩展名的文件:

cpio -div file.cpio
或cpio -divc file.cpio
10.以.rpm为扩展名的文件安装:

rpm -i file.rpm
11.以.rpm为扩展名的文件解压缩：

rpm2cpio file.rpm | cpio -div
12.以.deb为扩展名的文件安装：

dpkg -i file.deb
13.以.deb为扩展名的文件解压缩:

dpkg-deb -fsys-tarfile file.deb | tar xvf - ar p
file.deb data.tar.gz | tar xvzf -
14.以.zip为扩展名的文件:

unzip file.zip

作者：leoatchina
链接：https://www.jianshu.com/p/ca41f32420d6
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。




大致总结了一下linux下各种格式的压缩包的压缩、解压方法。但是部分方法我没有用到，也就不全，希望大家帮我补充，我将随时修改完善，谢谢！ 
　　 
　　.tar 
　　解包：tar xvf FileName.tar 
　　打包：tar cvf FileName.tar DirName 
　　（注：tar是打包，不是压缩！） 
　　——————————————— 
　　.gz 
　　解压 1：gunzip FileName.gz 
　　解压2：gzip -d FileName.gz 
　　压缩：gzip FileName 
　　.tar.gz 和 .tgz 
　　解压：tar zxvf FileName.tar.gz 
　　压缩：tar zcvf FileName.tar.gz DirName 
　　——————————————— 
　　.bz2 
　　解压1：bzip2 -d FileName.bz2 
　　解压2：bunzip2 FileName.bz2 
　　压缩： bzip2 -z FileName 
　　.tar.bz2 
　　解压：tar jxvf FileName.tar.bz2        或tar --bzip xvf FileName.tar.bz2 
　　压缩：tar jcvf FileName.tar.bz2 DirName 
　　 ——————————————— 
　　.bz 
　　解压1：bzip2 -d FileName.bz 
　　解压2：bunzip2 FileName.bz 
　　压缩：未知 
　　.tar.bz 
　　解压：tar jxvf FileName.tar.bz 
　　压缩：未知 
　　——————————————— 
　　.Z 
　　解压：uncompress FileName.Z 
　　压缩：compress FileName 
　　.tar.Z 
　　解压：tar Zxvf FileName.tar.Z 
　　压缩：tar Zcvf FileName.tar.Z DirName 
　　——————————————— 
　　.zip 
　　解压：unzip FileName.zip 
　　压缩：zip FileName.zip DirName 
　　压缩一个目录使用 -r 参数，-r 递归。例： $ zip -r FileName.zip DirName 
　　——————————————— 
　　.rar 
　　解压：rar x FileName.rar 
　　压缩：rar a FileName.rar DirName 
　　 
　　rar 请到：http://www.rarsoft.com/download.htm 下载！ 
　　解压后请将rar_static拷贝到/usr /bin目录（其他由$PATH环境变量指定的目录也可以）： 
　　[root@www2 tmp]# cp rar_static /usr/bin/rar 
　　——————————————— 
　　.lha 
　　解压：lha -e FileName.lha 
　　压缩：lha -a FileName.lha FileName 
　　 
　　lha请到：http://www.infor.kanazawa-it.ac.jp/~ishii/lhaunix/下载！ 
　　>解压后请将 lha拷贝到/usr/bin目录（其他由$PATH环境变量指定的目录也可以）： 
　　[root@www2 tmp]# cp lha /usr/bin/ 
　　——————————————— 
　　.rpm 
　　解包：rpm2cpio FileName.rpm | cpio -div 
　　——————————————— 
　　.deb 
　　解包：ar p FileName.deb data.tar.gz | tar zxf - 
　　——————————————— 
　　.tar .tgz .tar.gz .tar.Z .tar.bz .tar.bz2 .zip .cpio .rpm .deb .slp .arj .rar .ace .lha .lzh .lzx .lzs .arc .sda .sfx .lnx .zoo .cab .kar .cpt .pit .sit .sea 
　　解压：sEx x FileName.* 
　　压缩：sEx a FileName.* FileName 
　　 
　　sEx只是调用相关程序，本身并无压缩、解压功能，请注意！ 
　　sEx请到： http://sourceforge.net/projects/sex下载！ 
　　解压后请将sEx拷贝到/usr/bin目录（其他由$PATH环境变量指定的目录也可以）： 
　　[root@www2 tmp]# cp sEx /usr/bin/　　Linux下常见文件解压方法及命令 
　　系统·System 
　　 
　　1.以.a为扩展名的文件: 
　　#tar xv file.a 
　　2.以.z为扩展名的文件: 
　　#uncompress file.Z 
　　3.以.gz为扩展名的文件: 
　　#gunzip file.gz 
　　4.以.bz2为扩展名的文件: 
　　#bunzip2 file.bz2 
　　5.以.tar.Z为扩展名的文件: 
　　#tar xvZf file.tar.Z 
　　或 #compress -dc file.tar.Z | tar xvf 
　　6.以.tar.gz/.tgz为扩展名的文件: 
　　#tar xvzf file.tar.gz 
　　或 gzip -dc file.tar.gz | tar xvf - 
　　7.以.tar.bz2为扩展名的文件: 
　　#tar xvIf file.tar.bz2 
　　或 bzip2 -dc file.tar.bz2 | xvf - 
　　8.以.cpio.gz/.cgz为扩展名的文件: 
　　#gzip -dc file.cgz | cpio -div 
　　9. 以.cpio/cpio为扩展名的文件: 
　　#cpio -div file.cpio 
　　或cpio -divc file.cpio 
　　10.以.rpm为扩展名的文件安装: 
　　#rpm -i file.rpm 
　　11.以.rpm为扩展名的文件解压缩： 
　　 #rpm2cpio file.rpm | cpio -div 
　　12.以.deb为扩展名的文件安装： 
　　#dpkg -i file.deb 
　　13.以.deb为扩展名的文件解压缩: 
　　#dpkg-deb -fsys-tarfile file.deb | tar xvf - ar p 
　　file.deb data.tar.gz | tar xvzf - 
　　14.以.zip为扩展名的文件: 
　　#unzip file.zip 
　　在linux下解压Winzip格式的文件 
　　要是装了jdk的话，可以用 jar命令；还可以使用unzip命令。 
　　直接解压.tar.gz文件 
　　xxxx.tar.gz文件使用tar带zxvf参数，可以一次解压开。XXXX为文件名。 例如： 
　　$tar zxvf xxxx.tar.gz 各种压缩文件的解压（安装方法） 
　　 
　　文件扩展名 解压（安装方法） 
　　　 
　　.a ar xv file.a 
　　.Z uncompress file.Z 
　　.gz gunzip file.gz 
　　.bz2 bunzip2 file.bz2 
　　.tar.Z tar xvZf file.tar.Z 
　　compress -dc file.tar.Z | tar xvf - 
　　.tar.gz/.tgz tar xvzf file.tar.gz 
　　gzip -dc file.tar.gz | tar xvf - 
　　.tar.bz2 tar xvIf file.tar.bz2 
　　bzip2 -dc file.tar.bz2 | xvf - 
　　.cpio.gz/.cgz gzip -dc file.cgz | cpio -div 
　　.cpio/cpio cpio -div file.cpio 
　　cpio -divc file.cpio 
　　.rpm/install rpm -i file.rpm 
　　.rpm/extract rpm2cpio file.rpm | cpio -div 
　　.deb/install dpkg -i file.deb 
　　.deb/exrtact dpkg-deb -fsys-tarfile file.deb | tar xvf - 
　　ar p file.deb data.tar.gz | tar xvzf - 
　　.zip unzip file.zip 
　　 
　　 
　　bzip2 -d myfile.tar.bz2 | tar xvf 
　　 
　　 
　　tar xvfz myfile.tar.bz2 
　　 
　　 
　　x 是解压 
　　v 是复杂输出 
　　f 是指定文件 
　　z gz格式 
　　 
　　 
　　gzip 
　　gzip[选项]要压缩（或解压缩）的文件名 
　　-c将输出写到标准输出上，并保留原有文件。 
　　-d将压缩文件压缩。 
　　-l对每个压缩文件，显示下列字段：压缩文件的大小，未压缩文件的大小、压缩比、未压缩文件的名字 
　　-r递归式地查找指定目录并压缩或压缩其中的所有文件。 
　　-t测试压缩文件是正完整。 
　　-v对每一个压缩和解压缩的文件，显示其文件名和压缩比。 
　　-num-用指定的数字调整压缩的速度。 
　　举例： 
　　把/usr目录并包括它的子目录在内的全部文件做一备份，备份文件名为usr.tar 
　　tar cvf usr.tar /home 
　　把/usr 目录并包括它的子目录在内的全部文件做一备份并进行压缩，备份文件名是usr.tar.gz 
　　tar czvf usr.tar.gz /usr 
　　压缩一组文件，文件的后缀为tar.gz 
　　#tar cvf back.tar /back/ 
　　#gzip -q back.tar 
　　or 
　　#tar cvfz back.tar.gz /back/ 
　　释放一个后缀为tar.gz 的文件。 
　　#tar zxvf back.tar.gz 
　　#gzip back.tar.gz 
　　#tar xvf back.tar
  
  
  
  
  在Linux下面如何去压缩文件或者目录呢？

在这里我们将学习zip, tar, tar.gz和tar.bz2等压缩格式的基本用法。



首先了解下Linux里面常用的压缩格式。

 

在 我们探究这些用法之前，我想先跟大家分享一下使用不同压缩格式的经验。当然，我这里讲到的只是其中的一些用法，除我讲到的之外，他们还有更多的地 方值得 我们探讨。我已经意识到我需要了解两到三种压缩格式，才能更好的使用他们。zip格式是第一个需要了解的格式。因为它实际上已成为压缩文件的标准选 择， 而且它在windows上也能使用。我经常用zip格式压缩那些需要共享给windows用户的文件。如果只是共享给linux用户或者Mac用户， 那 我偏向于选择tar.gz格式。

 

ZIP ——zip可能是目前使用得最多的文档压缩格式。

它最大的优点就是在不同的操作系统平台，比如Linux， Windows以及Mac OS上使用。缺点就是支持的压缩率不是很高，而tar.gz和tar.gz2在压缩率方面做得非常好。闲话少说，我们步入正题吧：

我们可以使用下列的命令压缩一个目录：

# zip -r archive_name.zip directory_to_compress

 

下面是如果解压一个zip文档：

# unzip archive_name.zip

 

TAR

Tar是在Linux中使用得非常广泛的文档打包格式。它的好处就是它只消耗非常少的CPU以及时间去打包文件，他仅仅只是一个打包工具，并不负责压缩。

下面是如何打包一个目录：

# tar -cvf archive_name.tar directory_to_compress

 

如何解包：

# tar -xvf archive_name.tar.gz

 

上面这个解包命令将会将文档解开在当前目录下面。当然，你也可以用这个命令来捏住解包的路径：

# tar -xvf archive_name.tar -C /tmp/extract_here/

 

TAR.GZ

这种格式是我使用得最多的压缩格式。它在压缩时不会占用太多CPU的，而且可以得到一个非常理想的压缩率。

使用下面这种格式去压缩一个目录：

# tar -zcvf archive_name.tar.gz directory_to_compress

 

解压缩：

# tar -zxvf archive_name.tar.gz

 

上面这个解包命令将会将文档解开在当前目录下面。当然，你也可以用这个命令来捏住解包的路径：

# tar -zxvf archive_name.tar.gz -C /tmp/extract_here/

 

TAR.BZ2

这种压缩格式是我们提到的所有方式中压缩率最好的。当然，这也就意味着，它比前面的方式要占用更多的CPU与时间。

这个就是你如何使用tar.bz2进行压缩。

# tar -jcvf archive_name.tar.bz2 directory_to_compress

 

上面这个解包命令将会将文档解开在当前目录下面。当然，你也可以用这个命令来捏住解包的路径：

# tar -jxvf archive_name.tar.bz2 -C /tmp/extract_here/

 

数据压缩是非常有用的，尤其是对于备份来说。所以，你现在应该考虑在你的备份脚本中使用你在这里学到的压缩方式备份你基本的规则文件以减小你备份文件的大小。

 

过段时间之后，你就会意识到，在压缩率与CPU占用时间上会有一个平衡，你也要学会如何去权衡什么时候你需要一个快但是压缩率低，什么时候需要一个压缩率高但是CPU点用高的压缩方式，然后你才能避免无谓的空间与时间。





压缩

tar –cvf jpg.tar *.jpg //将目录里所有jpg文件打包成tar.jpg

tar –czf jpg.tar.gz *.jpg //将目录里所有jpg文件打包成jpg.tar后，并且将其用gzip压缩，生成一个gzip压缩过的包，命名为jpg.tar.gz

tar –cjf jpg.tar.bz2 *.jpg //将目录里所有jpg文件打包成jpg.tar后，并且将其用bzip2压缩，生成一个bzip2压缩过的包，命名为jpg.tar.bz2

tar –cZf jpg.tar.Z *.jpg //将目录里所有jpg文件打包成jpg.tar后，并且将其用compress压缩，生成一个umcompress压缩过的包，命名为jpg.tar.Z

rar a jpg.rar *.jpg //rar格式的压缩，需要先下载rar for linux

zip jpg.zip *.jpg //zip格式的压缩，需要先下载zip for linux

解压

tar –xvf file.tar //解压 tar包

tar -xzvf file.tar.gz //解压tar.gz

tar -xjvf file.tar.bz2 //解压 tar.bz2

tar –xZvf file.tar.Z //解压tar.Z

unrar e file.rar //解压rar

unzip file.zip //解压zip


总结：

1、*.tar 用 tar –xvf 解压

2、*.gz 用 gzip -d或者gunzip 解压

3、*.tar.gz和*.tgz 用 tar –xzf 解压

4、*.bz2 用 bzip2 -d或者用bunzip2 解压

5、*.tar.bz2用tar –xjf 解压

6、*.Z 用 uncompress 解压

7、*.tar.Z 用tar –xZf 解压

8、*.rar 用 unrar e解压

9、*.zip 用 unzip 解压