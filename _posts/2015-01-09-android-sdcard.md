---
layout: black_white
title: 浅谈android中的目录结构
---

***

在开发android应用的过程中，总要去调试APP,安装时又想去了解android的目录结构。然后搜到了一点材料。

Google Android手机的软件为了安全性和稳定性都是默认安装到手机内存里，但是手机内存有限，所以我们会做app2sd操作，来让我们安装的软件放到sd卡上，这个操作是需要rom的支持的。

Android 2.2 可以将手机程序安装在外置的sd卡上，也就是我们平常所说的app2sd。但是，官方的app2sd(application to Secure Digital)**[Google的Android系统是基于Linux的，所以存储卡上本身的Fat格式是不会被识别的，所以我们要分区（第二分区）出来，格式化成Linux认识的ext2或3或4格式，再用链接命令，把这个分区映射成一个系统文件夹system/sd，把所有的软件装到这个“文件夹”下，这就是App2sd功能的操作过程。   同时安装在SD卡中的软件或者游戏还是需要占用手机的内存的，因为放在SD卡当中的只是文件本身，而运行文件还是放在手机内存中。因此，App2sd的操作其实是牺牲了一部分软件的速度和稳定性来换取更多的手机内存安装更多的软件。]**非常鸡肋，需要软件自身支持安装在内存卡上才可以，也就是说用官方的app2sd，要把程序安装在内存卡上，并不是我们使用者说了算，而是软件开发者说了算。经测试安装60多个软件，其中仅有可怜的5个程序能使用官方的app2sd安装在内存卡上。所以，官方的这个app2sd就是忽悠人的。当然，现在很多第三方ROM都自带了第三方的app2sd，可以将任何程序都安装在sd卡上。

在正式介绍app2sd之前，我先要介绍下android系统的几个比较重要的目录，这是理解后面内容的基础。

>/system 存放的是rom的信息； 

>/system/app 存放rom本身附带的软件即系统软件； 

>/system/data 存放/system/app 中核心系统软件的数据文件信息。

>/data 存放的是用户的软件信息（非自带rom安装的软件）；

>/data/app 存放用户安装的软件；

>/data/data 存放所有软件（包括/system/app 和 /data/app 和 /mnt/asec中装的软件）的一些lib和xml文件等数据信息；

>/data/dalvik-cache 存放程序的缓存文件，这里的文件都是可以删除的。

>/mnt 目录，熟悉linux的人都清楚，linux默认挂载外部设备都会挂到这个目录下面去，如将sd卡挂载上去后，会生成一个/mnt/sdcard 目录。

>/sdcard 目录，这是一个软链接（相当于windows的文件夹的快捷方式），链接到/mnt/sdcard 目录，即这个目录的内容就是sdcard的内容。

在Android 2.2之后的版本允许将应用程序安装于SD卡，每一个安装在SD卡的应用程序，都可以在SD卡中的/sdcard/.android_secure 目录里找到名称中有出现它的程序名，和副文件名为asec的经过特殊加密处理后的档案。当SD卡挂载于手机时，/mnt/sdcard/.android_secure 目录会被映射到/mnt/asec 目录和 /mnt/secure 目录。其中/mnt/asec  目录中主要是程序的安装目录，包括其执行文件和lib文件等；而/mnt/secure 目录中就存放程序加密后的档案。也就是说，在/mnt路径下看到的/mnt/asec目录和/mnt/secure目录并不是真正存在在手机内存或者sd卡的分区挂载目录，它们只是/mnt/sdcard/.android_secure目录的一个影像而已。

因此，用户程序安装到到sd卡上后，其内容可能分散到：/mnt/asec , /mnt/secure , /data/data 。

要实现app2sd，目前比较流行有两种方案，分别是app2ext 和 data2ext，下面分别介绍下这2种方案。

在Linux文件系统中，有一种特别的文件叫“软链接”，类似于Windows下的快捷方式，软链接可以把一个文件或者文件夹映射到别的地方，一个例子如上面介绍的/sdcard 就是/mnt/sdcard 的软链接。

**app2ext**的原理是，删除data区中的app文件夹，然后在sd卡的ext分区上创建一个app文件，并通过软链接映射到data区。这样系统会以为，app这个软链接是一个真实的文件夹，会把程序都安装在里面，但实际上，这些程序都安装到卡上了。但由于操作系统并不知道，所以这种情况下，我们依然看到系统显示这个程序是安装在“内置空间”的。

**data2ext**则更彻底，它不是用软链接，而是直接用“挂载”功能，Linux下所有的存储设备都必须挂载成一个文件夹才能进行文件操作（如sd卡就挂载在/mnt/sdcard目录下面）。data文件夹本来是对应手机内部Flash中的一个分区（为了保持术语的准确，这里要把内部Flash和内存相区别，内部Flash是ROM，内存是RAM）。而data2ext则是修改了挂载对应关系，使data文件夹挂载的不是内置Flash，而是sd卡的整个ext分区。这样，不仅是app，连存储程序设置的data和缓存dalvik-cache都会存储到sd卡中。

可以看到，dalvik-cache和data这两个文件夹的位置，是这两种方式的一个重大区别。其中dalvik-cache是虚拟机预编译缓存，data（不同于/data，这个是/data/data）是存储程序数据的地方，例如游戏的存档记录，软件的配置信息等。这样有什么区别，区别在于假如你重刷了ROM，app2ext的话，所有的程序都可以保留，但是这些程序的配置信息和游戏的存档都会丢失。而data2ext则可以连同配置和存档都保留，但是dalvik-cache也是一个容易积累垃圾的地方，这些垃圾也会一同保留。
data2ext由于是把整个data分区都放在sd卡上，因此，我们刷ROM需要WIPE的时候，这个data分区的内容就可能不会被wipe，这可以保存用户的个人资料，但是也可能造成系统莫名其妙的故障。

[原文链接:](http://www.cnblogs.com/codeworker/archive/2011/12/30/2307834.html)

***