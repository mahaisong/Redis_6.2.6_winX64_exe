# Redis_6.2.6_winX64_exe
Redis_6.2.6_打包WinX64，exe
下载地址：
https://raw.githubusercontent.com/mahaisong/Redis_6.2.6_winX64_exe/master/Redis6.2.6Win64Exe.rar


打包的步骤参见doc文档： 下面是无图版本说明打包步骤。

警告：WIN平台不能使用redis 扩展插件module 功能(so后缀文件)，只能使用redis自身功能。

Redis的代码编译需要gcc和make，这都是linux环境上的。
我要在win系统能运行工具1个工具 搞定gcc make，还能把redis的代码搞成exe。
选MSYS2这是一个专用的工具和库的集合，将linux代码编译打包构建为，能在windows运行的软件。 

下载安装msys2
www.msys2.org官网下载慢，找国内的源下载最新的：
https://mirrors.tuna.tsinghua.edu.cn/msys2/distrib/x86_64/msys2-x86_64-20220128.exe。
（先换源）跟着官网安装走一波。更新pacman 要换一下国内的源。
换源：
安装目录 /etc/pacman.d/ 所有文件都换

将文件中清华tsinghua的源，放在第一行


运行软件
打开msys2.exe，
执行官网操作更新一下：pacman是工具包管理器。
Pacman -Syu  需要就按Y，直到自动关闭。



安装GCC和MAKE
gcc和make了：
打开msys2.exe输入： pacman -S gcc make


打包redis
官网下载redis6.2.6 源代码
https://download.redis.io/releases/redis-6.2.6.tar.gz

放到C盘根目录下，msys2.exe也切换到C盘根目录下


 

执行make
输入命令make PREFIX=xxxx install
PREFIX 是打包后输出的目录。我这里放到了C盘的tmpinstall目录下。
waring跳过、error错误要解决。


打包exe成功----恢复dlfcn.h文件

解决Dl_info报错
Dl_info没找到，是因为msys2内(C:\msys64\usr\include\dlfcn.h)代码有判断，先copy外面备份，再删除#if 和 #endif



准备：运行redis
Redis虽然打包成功了。但是运行还需要一些库和配置文件，一一复制过来。


复制msys-2.0.dll
在msys2文件夹搜索msys-2.0.dll

复制conf配置文件
去redis源码目录找redis.conf 和 sentinel.conf，复制过来。

验证：运行服务端+客户端
启动成功！
Exe文件夹全部挪到你正常使用的文件路径。 
源代码文件全部删除。



 