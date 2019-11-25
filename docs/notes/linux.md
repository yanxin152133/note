# Linux命令
## 软件包管理工具
### rpm
rpm是RedHat Package Manager(RedHat软件包管理工具)。
         
**语法：**
        
```html
rpm(选项)(参数)
```
            
**选项：**
        
```html
-a：查询所有套件；
-b<完成阶段><套件档>+或-t <完成阶段><套件档>+：设置包装套件的完成阶段，并指定套件档的文件名称；
-c：只列出组态配置文件，本参数需配合"-l"参数使用；
-d：只列出文本文件，本参数需配合"-l"参数使用；
-e<套件档>或--erase<套件档>：删除指定的套件；
-f<文件>+：查询拥有指定文件的套件；
-h或--hash：套件安装时列出标记；
-i：显示套件的相关信息；
-i<套件档>或--install<套件档>：安装指定的套件档；
-l：显示套件的文件列表；
-p<套件档>+：查询指定的RPM套件档；
-q：使用询问模式，当遇到任何问题时，rpm指令会先询问用户；
-R：显示套件的关联性信息；
-s：显示文件状态，本参数需配合"-l"参数使用；
-U<套件档>或--upgrade<套件档>：升级指定的套件档；
-v：显示指令执行过程；
-vv：详细显示指令执行过程，便于排错。
```
           
**参数：**
        
```html
软件包：指定要操纵的rpm软件包
```
         
**常用命令组合：**      
        
```html
－ivh：安装显示安装进度--install--verbose--hash
－Uvh：升级软件包--Update；
－qpl：列出RPM软件包内的文件信息[Query Package list]；
－qpi：列出RPM软件包的描述信息[Query Package install package(s)]；
－qf：查找指定文件属于哪个RPM软件包[Query File]；
－Va：校验所有的RPM软件包，查找丢失的文件[View Lost]；
－e：删除包
```
           
```bash
rpm -q samba //查询程序是否安装

rpm -ivh  /media/cdrom/RedHat/RPMS/samba-3.0.10-1.4E.i386.rpm //按路径安装并显示进度
rpm -ivh --relocate /=/opt/gaim gaim-1.3.0-1.fc4.i386.rpm    //指定安装目录

rpm -ivh --test gaim-1.3.0-1.fc4.i386.rpm　　　 //用来检查依赖关系；并不是真正的安装；
rpm -Uvh --oldpackage gaim-1.3.0-1.fc4.i386.rpm //新版本降级为旧版本

rpm -qa | grep httpd　　　　　 ＃[搜索指定rpm包是否安装]--all搜索*httpd*
rpm -ql httpd　　　　　　　　　＃[搜索rpm包]--list所有文件安装目录

rpm -qpi Linux-1.4-6.i368.rpm　＃[查看rpm包]--query--package--install package信息
rpm -qpf Linux-1.4-6.i368.rpm　＃[查看rpm包]--file
rpm -qpR file.rpm　　　　　　　＃[查看包]依赖关系
rpm2cpio file.rpm |cpio -div    ＃[抽出文件]

rpm -ivh file.rpm 　＃[安装新的rpm]--install--verbose--hash
rpm -ivh

rpm -Uvh file.rpm    ＃[升级一个rpm]--upgrade
rpm -e file.rpm      ＃[删除一个rpm包]--erase
```
        
### yum
>基于RPM的软件包管理器
            
yum命令是在Fedora和RedHat以及SUSE中基于rpm的软件包管理器，它可以使系统管理人员交互和自动化地更新与管理RPM软件包，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包，无须繁琐地一次次下载、安装。
         
yum提供了查找、安装、删除某一个、一组甚至全部软件包的命令，而且命令简洁而又好记。
           
**语法：**       
         
```html
yum(选项)(参数)
```
        
**选项：**
          
```html
-h：显示帮助信息；
-y：对所有的提问都回答“yes”；
-c：指定配置文件；
-q：安静模式；
-v：详细模式；
-d：设置调试等级（0-10）；
-e：设置错误等级（0-10）；
-R：设置yum处理一个命令的最大等待时间；
-C：完全从缓存中运行，而不去下载或者更新任何头文件。
```
        
**参数：**
        
```html
install：安装rpm软件包；
update：更新rpm软件包；
check-update：检查是否有可用的更新rpm软件包；
remove：删除指定的rpm软件包；
list：显示软件包的信息；
search：检查软件包的信息；
info：显示指定的rpm软件包的描述信息和概要信息；
clean：清理yum过期的缓存；
shell：进入yum的shell提示符；
resolvedep：显示rpm软件包的依赖关系；
localinstall：安装本地的rpm软件包；
localupdate：显示本地rpm软件包进行更新；
deplist：显示rpm软件包的所有依赖关系。
```
        
**实例：**
        
部分常用的命令包括：      
- 自动搜索最快经i选哪个插件：`yum install yum-fastestmirror`
- 安装yum图形窗口插件：`yum install yumex`
- 查看可能批量安装的列表：`yum grouplist`
          
常用命令如下：      
        
```bash
## 安装
yum install     # 全部安装
yum install package1    # 安装指定的安装包package1
yum groupinsall group1    # 安装程序组group1


## 更新和升级
yum update        # 全部更新
yum update package1     # 更新指定程序包package1
yum check-update      # 检查可更新的程序
yum upgrade package   # 升级指定程序包package1
yum groupupdate group1   # 升级程序组group1


## 查找和显示
# 检查MySQL是否已经安装
yum list installed |grep mysql
yum list installed mysql*

yum info package1   # 显示安装包信息package1
yum list     # 显示所有已经安装和可以安装的程序包
yum list package1   # 显示指定程序包安装情况package1
yum groupinfo group1    # 显示程序组group1信息
yum search string      # 根据关键字string查找安装包


# 删除程序
yum remove package1    # 删除程序包package1
yum groupremove group   # 删除程序组group1
yum deplist package1    # 查看程序package1依赖情况


# 清除缓存
yum clean packages    # 清除缓存目录下的软件包
yum clean headers   # 清除缓存目录下的headers
yum clean oldheaders   # 清除缓存目录下旧的headers
```
         
### dpkg-deb
>Debian Linux下的软件包管理工具
          
dpkg-deb命令是Debian Linux下的软件包管理工具，它可以对软件包执行打包和解包操作以及提供软件包信息。
           
**语法：**
        
```html
dpkg-deb(选项)(参数)
```
        
**选项：**
        
```html
-c：显示软件包中的文件列表；
-e：将主控信息解压；
-f：把字段内容打印到标准输出；
-x：将软件包中的文件释放到指定目录下；
-X：将软件包中的文件释放到指定目录下，并显示释放文件的详细过程；
-w：显示软件包的信息；
-l：显示软件包的详细信息；
-R：提取控制信息和存档的清单文件；
-b：创建debian软件包。
```
           
**参数：**
        
```html
文件：指定要操作的“.deb”软件包的全名或软件名
```
          
**常用命令：**
        
1. 解压程序文件。
         
```bash
dpkg-deb -x drcom-pum_1.0-0ubuntu1~ppa1~jaunty1_i386.deb drcom
```
         
2. 解压控制文件。
        
```bash
dpkg-deb -e drcom-pum_1.0-0ubuntu1~ppa1~jaunty1_i386.deb drcom/DEBIAN
```
       
3. 打包生成deb文件。
        
```bash
dpkg-deb -b drcom drcom_1.4.8.2_i386.deb
```
         
4. 查询deb包中的文件内容。
        
```bash
dpkg-deb -c demo.deb
```
           
### apt-get
>Debian Linux发行版中的APT软件包管理工具。
         
apt-get命令是Debian Linux发行版中的APT软件包管理工具。所有基于Debian的发行都使用这个包管理系统。deb包可以把一个应用的文件包在一起，答题就如同Windows上的安装文件。
        
**语法：**
         
```html
apt-get(选项)(参数)
```
       
**选项：**
        
```bash
-c:指定配置文件
```
       
**参数：**
         
- 管理指令：对APT软件包的管理操作
- 软件包：指定要操纵的软件包
           
**常用命令：**
         
```bash
## 更新
apt-get update


## 安装一个新软件包
apt-get install packagename


## 卸载一个已安装的软件包（保留配置文件）
apt-get remove packagename


## 卸载一个已安装的软件包（删除配置文件）
apt-get -purge remove packagename


## 删除已经卸载掉的软件，节省硬盘空间
apt-get autoclean apt


## 更新所有已安装的软件包
apt-get upgrade
```
       
### pacman
参考：[pacman](https://wiki.archlinux.org/index.php/Pacman_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
                 
## 系统信息
### uname
>显示Linux系统信息
         
uname命令用于打印当前系统相关信息（内核版本号、硬件架构、主机名称和操作系统类型等）。
           
**语法：**
       
```html
uname(选项)
```
        
**选项：**
       
```bash
-a或--all：显示全部的信息
-m或--machine：显示电脑类型
-n或-nodename：显示在网络上的主机名称
-r或--release：显示操作系统的发行编号；
-s或--sysname：显示操作系统名称；
-v：显示操作系统的版本；
-p或--processor：输出处理器类型或"unknown"；
-i或--hardware-platform：输出硬件平台或"unknown"；
-o或--operating-system：输出操作系统名称；
--help：显示帮助；
--version：显示版本信息
```
             
**常用命令：**
        
查看系统全部信息：
        
```bash
[root@localhost ~]# uname    #单独使用uname命令时相当于uname -s
Linux

[root@localhost ~]# uname -a
Linux localhost 2.6.18-348.6.1.el5 #1 SMP Tue May 21 15:34:22 EDT 2013 i686 i686 i386 GNU/Linux

[root@localhost ~]# uname -m
i686

[root@localhost ~]# uname -n
localhost

[root@localhost ~]# uname -r
2.6.18-4-686

[root@localhost ~]# uname -s
Linux

[root@localhost ~]# uname -v
#1 SMP Tue May 21 15:34:22 EDT 2013

[root@localhost ~]# uname -p
i686

[root@localhost ~]# uname -i
i386

[root@localhost ~]# uname -o
GNU/Linux

[root@localhost ~]# uname --version
uname (GNU coreutils) 8.28
Copyright (C) 2017 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David MacKenzie.
```
         
### arch
>显示当前主机的硬件架构类型
        
arch命令用于显示当前主机的硬件架构类型。arch命令等同于命令name -m 在当前的Linux系统下，arch命令输出结果有:i386、i486、i586、alpha、sparc、arm、m68k、mips、ppc、i686等。
         
**语法：**
        
```html
arch [选项]...
```
        
**选项：**
       
```html
--help 显示此帮助信息并退出
--version  显示版本信息并退出
```
            
**常用命令：**
         
```bash
root@001:~# arch
x86_64
```
         
### dmidecode
>在Linux系统下获取有关硬件方面的信息。
              
dmidecode命令 可以让你在Linux系统下获取有关硬件方面的信息。dmidecode的作用是将DMI数据库中的信息解码，以可读的文本方式显示。由于DMI信息可以人为修改，因此里面的信息不一定是系统准确的信息。dmidecode遵循SMBIOS/DMI标准，其输出的信息包括BIOS、系统、主板、处理器、内存、缓存等等。
           
DMI（Desktop Management Interface,DMI）就是帮助收集电脑系统信息的管理系统，DMI信息的收集必须在严格遵照SMBIOS规范的前提下进行。SMBIOS（System Management BIOS）是主板或系统制造者以标准格式显示产品管理信息所需遵循的统一规范。SMBIOS和DMI是由行业指导机构Desktop Management Task Force(DMTF)起草的开放性的技术标准，其中DMI设计适用于任何的平台和操作系统。
            
DMI充当了管理工具和系统层之间接口的角色。它建立了标准的可管理系统更加方便了电脑厂商和用户对系统的了解。DMI的主要组成部分是Management Information Format(MIF)数据库。这个数据库包括了所有有关电脑系统和配件的信息。通过DMI，用户可以获取序列号、电脑厂商、串口信息以及其它系统配件信息。
                  
**语法：**
         
```html
dmicode [选项]
```
        
**选项：**
         
```bash
-d：(default:/dev/mem)从设备文件读取信息，输出内容与不加参数标准输出相同。
-h：显示帮助信息。
-s：只显示指定DMI字符串的信息。(string)
-t：只显示指定条目的信息。(type)
-u：显示未解码的原始条目内容。
--dump-bin file：将DMI数据转储到一个二进制文件中。
--from-dump FILE：从一个二进制文件读取DMI数据。
-V：显示版本信息。
```
        
**常用命令：**
        
```bash
dmidecode -t 1  # 查看服务器信息
dmidecode | grep 'Product Name' # 查看服务器型号 
dmidecode |grep 'Serial Number' # 查看主板的序列号 
dmidecode -t 2  # 查看主板信息
dmidecode -s system-serial-number # 查看系统序列号 
dmidecode -t memory # 查看内存信息 
dmidecode -t 11 # 查看OEM信息 
dmidecode -t 17 # 查看内存条数
dmidecode -t 16 # 查询内存信息
dmidecode -t 4  # 查看CPU信息

cat /proc/scsi/scsi # 查看服务器硬盘信息
```
         
### hdparm
>显示与设定硬盘的参数
           
hdparm命令提供了一个命令行的接口用于读取和设置IDE或SCSI硬盘参数。
                
**语法：**
        
```html
hdparm(选项)(参数)
```
        
**选项：**
        
```html
-a<快取分区>：设定读取文件时，预先存入块区的分区数，若不加上<快取分区>选项，则显示目前的设定；
-A<0或1>：启动或关闭读取文件时的快取功能；
-c<I/O模式>：设定IDE32位I/O模式；
-C：检测IDE硬盘的电源管理模式；
-d<0或1>：设定磁盘的DMA模式；
-f：将内存缓冲区的数据写入硬盘，并清楚缓冲区；
-g：显示硬盘的磁轨，磁头，磁区等参数；
-h：显示帮助；
-i：显示硬盘的硬件规格信息，这些信息是在开机时由硬盘本身所提供；
-I：直接读取硬盘所提供的硬件规格信息；
-k<0或1>：重设硬盘时，保留-dmu参数的设定；
-K<0或1>：重设硬盘时，保留-APSWXZ参数的设定；
-m<磁区数>：设定硬盘多重分区存取的分区数；
-n<0或1>：忽略硬盘写入时所发生的错误；
-p<PIO模式>：设定硬盘的PIO模式；
-P<磁区数>：设定硬盘内部快取的分区数；
-q:在执行后续的参数时，不在屏幕上显示任何信息；
-r<0或1>:设定硬盘的读写模式；
-S<时间>:设定硬盘进入省电模式前的等待时间；
-t;评估硬盘的读取效率；
-T：评估硬盘快取的读取效率；
-u<0或1>：在硬盘存取时，允许其他中断要求同时执行；
-v：显示硬盘的相关设定；
-w<0或1>：设定硬盘的写入快取；
-X<传输模式>：设定硬盘的传输模式；
-y：使IDE硬盘进入省电模式；
-Y：使IDE硬盘进入睡眠模式；
-Z：关闭某些Seagate硬盘的自动省电功能。
```

**参数：**
           
```html
设备文件：指定id驱动对应的设备文件名
```

**常用命令：**

1. 显示硬盘的相关设置。
          
```bash
root@001:~# hdparm /dev/vda

/dev/vda:
 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 83220[柱面数]/16[磁头数]/63[扇区数], sectors = 83886080[总扇区数], start = 0[起始扇区数]
```
          
2. 显示硬盘的柱面、磁头、扇区数。
          
```bash
root@001:~# hdparm -g /dev/vda

/dev/vda:
 geometry      = 83220[柱面数]/16[磁头数]/63[扇区数], sectors = 83886080[总扇区数], start = 0[起始扇区数]

```
       
3. 测试硬盘的读取速度。
         
```bash
root@001:~# hdparm -t /dev/vda

/dev/vda:
 Timing buffered disk reads: 358 MB in  3.52 seconds = 101.76 MB/sec
```
         
4. 测试硬盘缓存的读取速度。
          
```bash
root@001:~# hdparm -T /dev/vda

/dev/vda:
 Timing cached reads:   17490 MB in  2.00 seconds = 8765.89 MB/sec
```
        
5. 检查硬盘的电源管理模式。
         
```bash
root@001:~# hdparm -C /dev/vda

/dev/vda:
 drive state is:  unknown
```
         
6. 查询并设置硬盘多重扇区存取的扇区数，以增进硬盘的存取效率。
            
```bash
root@001:~# hdparm -m /dev/vda

/dev/vda:
 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
```
            
7. 硬盘坏道修复方法。
           
```bash
## 检查
smartctl -l selftest /dev/sda


## 卸载
umount /dev/sda*


## 修复
badblocks /dev/sda
```
         
### cat
>连接多个文件并打印到标准输出。
              
**语法：**
          
```bash
cat [OPTION]...[FILE]...
```
                              
**主要用途：**
           
- 显示文件内容，如果没有文件或文件为-则读取标准输入。
- 将多个文件的内容进行连接并打印到标准输出。
- 显示文件内容中的不可见字符（控制字符、换行符、制表符等）
             
**参数**
        
FILE（可选）：要处理的文件，可以为一或多个。
            
**选项：**
         
```bash
长选项与短选项等价

-A, --show-all           等价于"-vET"组合选项。
-b, --number-nonblank    只对非空行编号，从1开始编号，覆盖"-n"选项。
-e                       等价于"-vE"组合选项。
-E, --show-ends          在每行的结尾显示'$'字符。
-n, --number             对所有行编号，从1开始编号。
-s, --squeeze-blank      压缩连续的空行到一行。
-t                       等价于"-vT"组合选项。
-T, --show-tabs          使用"^I"表示TAB（制表符）。
-u                       POSIX兼容性选项，无意义。
-v, --show-nonprinting   使用"^"和"M-"符号显示控制字符，除了LFD（line feed，即换行符'\n'）和TAB（制表符）。

--help                   显示帮助信息并退出。
--version                显示版本信息并退出。
```
         
**返回值：**
        
返回状态为成功除非给出了非法选项或非法参数。
       
**常用命令：**

常规：      
             
```bash
# 合并显示多个文件
cat ./1.log ./2.log ./3.log
# 显示文件中的非打印字符、tab、换行符
cat -A test.log
# 压缩文件的空行
cat -s test.log
# 显示文件并在所有行开头附加行号
cat -n test.log
# 显示文件并在所有非空行开头附加行号
cat -b test.log
# 将标准输入的内容和文件内容一并显示
echo '######' |cat - test.log
```
           
打印系统信息：       
        
```bash
cat /proc/cpuinfo 显示CPU info的信息 
cat /proc/interrupts 显示中断 
cat /proc/meminfo 校验内存使用 
cat /proc/swaps 显示哪些swap被使用 
cat /proc/version 显示内核的版本 
cat /proc/net/dev 显示网络适配器及统计 
cat /proc/mounts 显示已加载的文件系统 
```