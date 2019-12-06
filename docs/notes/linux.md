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
        
### lspci
>显示当前主机的所有PCI总线信息。
        
lspci命令用于显示当前主机的所有PCI总线信息，以及所有已连接的PCI设备信息。
        
**语法：**
          
```html
lspci(选项)
```
             
**选项：**
         
```html
-v  使得 lspci 以冗余模式显示所有设备的详细信息。
-vv  使得 lspci 以过冗余模式显示更详细的信息 (事实上是 PCI 设备能给出的所有东西)。这些数据的确切意义没有在此手册页中解释，如果你想知道更多，请参照 /usr/include/linux/pci.h 或者 PCI 规范。
-n  以数字形式显示 PCI 生产厂商和设备号，而不是在 PCI ID 数据库中查找它们。
-x  以十六进制显示 PCI 配置空间 (configuration space) 的前64个字节映像 (标准头部信息)。此参数对调试驱动和 lspci 本身很有用。
-xxx  以十六进制显示所有 PCI 配置空间的映像。此选项只有 root 可用，并且很多 PCI 设备在你试图读取配置空间的未定义部分时会崩溃 (此操作可能不违反PCI标准，但是它至少非常愚蠢)。
-b  以总线为中心进行查看。显示所有 IRQ 号和记忆体地址，就像 PCI 总线上的卡看到的一样，而不是核心看到的内容。
-t  以树形方式显示包含所有总线、桥、设备和它们的连接的图表。
-s [[]:][][.[]]  仅显示指定总线、插槽上的设备或设备上的功能块信息。设备地址的任何部分都可以忽略，或以「*」代替 (意味著所有值)。所有数字都是十六进制。例如：「0：」指的是在0号总线上的所有设备；「0」指的是在任意总线上0号设备的所有功能块；「0.3」选择 了所有总线上0号设备的第三个功能块；「.4」则是只列出每一设备上的第四个功能块。
-d []:[]  只显示指定生产厂商和设备 ID 的设备。 这两个 ID 都以十六进制表示，可以忽略或者以「*」代替 (意味著所有值)。
-i  使用作为 PCI ID 数据库而不是使用预设的 /usr/share/hwdata/pci.ids。
-p   使用作为包含 PCI 总线信息的目录而不是使用预设的目录 /proc/bus/pci。
-m  以机器可读的方式转储 PCI 设备数据 (支持两种模式：普通和冗余)，便於稿本解析。
-M  使用总线映射模式，这种模式对总线进行全面地扫描以查明总线上的所有设备，包括配置错误的桥之后的设备。请注意，此操作只应在调试时使 用，并可能造成系统崩溃 (只在设备有错误的时候，但是不幸的是它们存在)，此命令只有 root 可以使用。同时，在不直接接触硬体的 PCI 访问模式中使用 -M 参数没有意义，因为显示的结果 (排除 lspci 中的 bug 的影响) 与普通的列表模式相同。
--version  显示 lspci 的版本。这个选项应当单独使用。

PCILIB 选项 PCILIB OPTIONS
PCI 工具使用 PCILIB (一种可移植的库，提供平台独立的函数来访问 PCI 配置空间)来和PCI卡交互。下面的选项用来控制库参数，特别是所用访问模式的指定。预设情况下，PCILIB 使用第一种可用的访问模式，不会显示任何调试信息。每一个开关选项都列出了一组它所支持的硬件/软软件列表。

-P  使用 linux 2.1 风格的配置，直接访问目录，而非 /proc/bus/pci 目录。(只能在linux 2.1或以上版本中使用)
-H1  通过 Intel 架构 1 来实现直接硬体访问。(只能用於 i386 及其相容机)
-H2  通过Intel 架构2来实现直接硬体访问。警告：此模式只能寻址任何总线上的前16个设备，并且在很多情况下相当不可靠。(只能用於 i386 及其相容机)
-S  使用 PCI 系统调用访问。(只能用於 Alpha 和 Ultra-Sparc 上的 Linux)
-F  从所给的包含 lspci -x命令输出的档案中获取相关信息。这在分析使用者提交的错误报告时很有用，因为你可以用任何方式来显示硬体配置信息而无需为了获取更多信息打扰使用者。(可用於所有系统)
-G  增加库的调试等级。(可用於所有系统)
```
           
**常用命令：**

1. 以树状结构显示PCI设备。

```bash
root@001:~# lspci -t
-[0000:00]-+-00.0
           +-01.0
           +-01.1
           +-01.2
           +-01.3
           +-02.0
           +-03.0
           +-04.0
           +-05.0
           \-06.0
```
        
2. 以树状结构显示PCI设备的层次关系以及详细信息。
         
```bash
root@001:~# lspci -tv
-[0000:00]-+-00.0  Intel Corporation 440FX - 82441FX PMC [Natoma]
           +-01.0  Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
           +-01.1  Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
           +-01.2  Intel Corporation 82371SB PIIX3 USB [Natoma/Triton II]
           +-01.3  Intel Corporation 82371AB/EB/MB PIIX4 ACPI
           +-02.0  Cirrus Logic GD 5446
           +-03.0  Red Hat, Inc. Virtio network device
           +-04.0  Red Hat, Inc. Virtio console
           +-05.0  Red Hat, Inc. Virtio block device
           \-06.0  Red Hat, Inc. Virtio memory balloon
```
           
### lsusb
>显示本机的USB设备列表信息。
          
lsusb命令用于显示本机的USB设备列表，以及USB设备的详细信息。
           
lsusb命令事一个学习USB驱动开发，认识USB设备的助手。
           
**语法：**
        
```html
lsusb(选项)
```
         
**选项：**
       
```html
-v：显示USB设备的详细信息；
-s<总线：设备号>仅显示指定的总线和（或）设备号的设备；
-d<厂商：产品>：仅显示指定厂商和产品编号的设备；
-t：以树状结构显示无理USB设备的层次；
-V：显示命令的版本信息。
```
         
**常用命令：**
       
1. 插入USB鼠标后执行lsusb的输出内容如下：     
       
```bash
Bus 005 Device 001: id 0000:0000 
Bus 001 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 006: ID 15d9:0a37 
Bus 002 Device 001: ID 0000:0000 
```
             
解释：
             
Bus 005
              
表示第五个usb主控制器(机器上总共有5个usb主控制器 -- 可以通过命令lspci | grep USB查看)
               
Device 006
                
表示系统给usb鼠标分配的设备号(devnum)，同时也可以看到该鼠标是插入到了第二个usb主控制器
               
```bash
006        usb_device.devnum
/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-2/devnum
```
          
ID 15d9:0a37
            
表示usb设备的ID（这个ID由芯片制造商设置，可以唯一表示该设备）
           
```bash
15d9    usb_device_descriptor.idVendor
0a37    usb_device_descriptor.idProduct
/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-2/idVendor
```
          
Bus 002 Device 006: ID 15d9:0a37       
Bus 002 Device 001: ID 0000:0000       
             
表示002号usb主控制器上接入了两个设备:
           
- 一个是usb根Hub -- 001
- 一个是usb鼠标 -- 006
            
### date
>显示或设置系统时间与日期。
              
**概要：**
        
```html
date [OPTION]... [+FORMAT]
date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]
```
         
**主要用途：**
        
- 转换时间到选定的格式，默认为当前
- 设置系统时间
         
**参数：**
          
format:输出的时间格式。
         
```html
format可用的转义序列如下：

%%      百分号
%a      当地缩写的工作日名称（例如，Sun）
%A      当地完整的工作日名称（例如，Sunday）
%b      当地缩写的月份名称（例如，Jan）
%B      当地完整的月份名称（例如，January）
%c      当地的日期和时间（例如，Thu Mar  3 23:05:25 2005）
%C      世纪，和%Y类似，但是省略后两位（例如，20）
%d      一月中的一天（例如，01）
%D      日期，等价于%m/%d/%y
%e      一月中的一天，格式使用空格填充，等价于%_d
%F      完整的日期；等价于%+4Y-%m-%d
%g      ISO标准计数周的年份的最后两位数字
%G      ISO标准计数周的年份，通常只对%V有用
%h      等价于%b
%H      小时，范围（00..23）
%I      小时，范围（00..23）
%j      一年中的一天，范围（001..366）
%k      小时，使用空格填充，范围（0..23），等价于%_H
%l      小时，使用空格填充，范围（1..12），等价于%_I
%m      月，范围（01..12）
%M      分钟，范围（00..59）
%n      换行符
%N      纳秒，范围（000000000..000000000）
%p      用于表示当地的AM或PM，如果未知则为空白
%P      类似于%p，但用小写表示
%q      季度，范围（1..4）
%r      当地以12小时表示的时钟时间（例如，11:11:04 PM）
%R      24小时每分钟；等价于%H:%M
%s      自协调世界时1970年01月01日00时00分以来的秒数
%S      秒数，范围（00..60）
%t      水平制表符
%T      时间；等价于%H:%M:%S
%u      一周中的一天（1..7），1代表星期一
%U      一年中的第几周，周日作为一周的起始（00..53）
%V      ISO标准计数周，该方法将周一作为一周的起始（01..53）
%w      一周中的一天（0..6），0代表星期天
%W      一年中的第几周，周一作为一周的起始（00..53）
%x      当地的日期表示（例如，12/31/99）
%X      当地的时间表示（例如，23:13:48）
%y      年份后两位数字，范围（00..99）
%Y      年份
%z      +hhmm格式的数值化时区格式（例如，-0400）
%:z     +hh:mm格式的数值化时区格式（例如，-04:00）
%::z    +hh:mm:ss格式的数值化时区格式（例如，-04:00:00）
%:::z   数值化时区格式，相比上一个格式增加':'以显示必要的精度（例如，-04，+05:30）
%Z      时区缩写（如EDT）

默认情况下，日期用零填充数字字段；以下可选的符号可以跟在'%'后面:

-      (连字符) 不要填充相应的字段。
_      (下划线) 使用空格填充相应的字段。
0      (数字0) 使用数字0填充相应的字段。
+      用数字0填充，未来年份大于4位数字则在前面加上'+'号。
^      允许的情况下使用大写。
#      允许的情况下将默认的大写转换为小写，默认的小写转换为大写。

在任何标志之后都有一个可选的字段宽度，如小数；然后是一个可选的修饰符，在可用的情况下，使用E来使用当地语言环境的替代表示，
使用O来使用当地语言环境的替代数字符号。
```

**选项：**

```html
长选项与短选项等价

-d, --date=STRING          解析字符串并按照指定格式输出，字符串不能是'now'。
--debug                    注释已解析的日期，并将有疑问的用法发送到标准错误。
-f, --file=DATEFILE        类似于--date; 一次从DATEFILE处理一行。
-I[FMT], --iso-8601[=FMT]  按照ISO 8601格式输出，FMT可以为'date'(默认)，'hours'，'minutes'，'seconds'，'ns'。
                           例如：2006-08-14T02:34:56-06:00
-R, --rfc-email            按照RFC 5322格式输出，例如: Mon, 14 Aug 2006 02:34:56 -0600
--rfc-3339=FMT             按照RFC 3339格式输出，FMT可以为'date', 'seconds','ns'中的一个，
                           例如：2006-08-14 02:34:56-06:00
-r, --reference=FILE       显示文件的上次修改时间。
-s, --set=STRING           根据字符串设置系统时间。
-u, --utc, --universal     显示或设置世界协调时(UTC)。
--help                     显示帮助信息并退出。
--version                  显示版本信息并退出。
```

**返回值：**

返回状态为成功除非给出了非法选项或非法参数。

**常用命令：**
          
```bash
# 格式化输出：
date +"%Y-%m-%d"
2009-12-07

# 输出昨天日期：
date -d "1 day ago" +"%Y-%m-%d"
2012-11-19

# 2秒后输出：
date -d "2 second" +"%Y-%m-%d %H:%M.%S"
2012-11-20 14:21.31

# 传说中的 1234567890 秒：
date -d "1970-01-01 1234567890 seconds" +"%Y-%m-%d %H:%M:%S"
# 或者
date -d@1234567890 +"%F %T"
# 输出结果
2009-02-13 23:02:30

# 时间格式转换：
date -d "2009-12-12" +"%Y/%m/%d %H:%M.%S"
# 输出结果
2009/12/12 00:00.00

# apache格式转换：
date -d "Dec 5, 2009 12:00:37 AM" +"%Y-%m-%d %H:%M.%S"
# 输出结果
2009-12-05 00:00.37

# 格式转换后时间游走：
date -d "Dec 5, 2009 12:00:37 AM 2 year ago" +"%Y-%m-%d %H:%M.%S"
# 输出结果
2007-12-05 00:00.37

# 时间加减操作：
date +%Y%m%d                   # 显示年月日
date -d "+1 day" +%Y%m%d       # 显示前一天的日期
date -d "-1 day" +%Y%m%d       # 显示后一天的日期
date -d "-1 month" +%Y%m%d     # 显示上一月的日期
date -d "+1 month" +%Y%m%d     # 显示下一月的日期
date -d "-1 year" +%Y%m%d      # 显示前一年的日期
date -d "+1 year" +%Y%m%d      # 显示下一年的日期

# 设定时间：
date -s                         # 设置当前时间，只有root权限才能设置，其他只能查看
date -s 20120523                # 设置成20120523，这样会把具体时间设置成00:00:00
date -s 01:01:01                # 设置具体时间，不会对日期做更改
date -s "01:01:01 2012-05-23"   # 这样可以设置全部时间
date -s "01:01:01 20120523"     # 这样可以设置全部时间
date -s "2012-05-23 01:01:01"   # 这样可以设置全部时间
date -s "20120523 01:01:01"     # 这样可以设置全部时间

# 有时需要检查一组命令花费的时间：
start=$(date +%s)
nmap wangchujiang.com &> /dev/null
end=$(date +%s)
difference=$(( end - start ))
# 显示执行时间
echo $difference seconds.

# 当你考虑输出带有时间的字符串时，例如（Current time: 2019/05/19）：
# 通常使用的方法：
echo "Current time: $(date +"%Y/%m/%d")"
# 另一种方法：
suffix='Current time:'
# 注意如果换成单引号就不能替换变量了。
date +"${suffix} %Y/%m/%d"
```
               
**注意:**
       
- 该命令是GNU coreutils包中的命令，相关的帮助信息请查看man -s 1 date或info coreutils 'date invocation'。
          
### cal
>显示当前日历或指定日期的日历。
          
cal命令用于显示当前日历，或者指定日期的日历，如果没有指定参数，则显示当前月份。
            
一个单一的参数指定要显示的年份（1-9999）；注意年份必须被完全地指定：`cal 89`不会显示1989年的日历，两个参数表示月份（1-12）和年份，如果没有指定参数，则显示当前月份的日历。
                 
一年从Jan 1（1月1日）开始。
           
格里高利历法改革(Gregorian Reformation)被认为发生于 1752 年 9 月 3 日. 在此之前, 多数国家已经认可这项改革(尽管有一些直到 20 世纪初才认可它). 那天之后的 10 天在这项改革被略去了, 所以那个月的日历有点不太寻常。
            
**语法：**
         
```html
cal [ -mjy ] [ 月份 ] [ 年份 ]
```
         
**选项：**
          
```html
-l # 显示单月输出；
-3 # 显示临近三个月的日历；
-s # 将星期日作为月的第一天；
-m # 显示星期一作为一周的第一天..  (缺省为星期日.)
-j # 显示儒略历的(Julian)日期 (以 1 为基的天数, 从 1 月 1 日开始计数) 
-y # 显示当前年份的日历
```
         
**参数：**
        
```html
月：指定月份；
年：指定年份。
```
          
**常用命令：**
         
1. 单独执行cal命令会打印出日历。
         
```bash
root@001:~# cal
   December 2019
Su Mo Tu We Th Fr Sa
 1  2  3  4  5  6  7
 8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 28
29 30 31
```
               
```bash
root@001:~# cal -j
       December 2019
 Su  Mo  Tu  We  Th  Fr  Sa
335 336 337 338 339 340 341
342 343 344 345 346 347 348
349 350 351 352 353 354 355
356 357 358 359 360 361 362
363 364 365
```
           
```bash
root@001:~# cal -3
   November 2019         December 2019          January 2020
Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa
                1  2   1  2  3  4  5  6  7            1  2  3  4
 3  4  5  6  7  8  9   8  9 10 11 12 13 14   5  6  7  8  9 10 11
10 11 12 13 14 15 16  15 16 17 18 19 20 21  12 13 14 15 16 17 18
17 18 19 20 21 22 23  22 23 24 25 26 27 28  19 20 21 22 23 24 25
24 25 26 27 28 29 30  29 30 31              26 27 28 29 30 31
```
            
### clock
>用于调整RTC时间。
           
clock命令用于调整RTC时间。RTC是电脑内建的硬件时间，执行这项指令可以显示现在时刻，调整硬件时钟的时间，将系统时间设成与硬件时钟之时间一致，或是把系统时间回存到硬件时钟。
          
**语法：**
          
```html
clock [--adjust][--debug][--directisa][--getepoch][--hctosys][--set --date="<日期时间>"]
[--setepoch --epoch=< >][--show][--systohc][--test][--utc][--version]
```
          
**选项：**
        
```html
--adjust 　第一次使用"--set"或"--systohc"参数设置硬件时钟，会在/etc目录下产生一个名称为adjtime的文件。当再次使用这两个参数调整硬件时钟，此文件便会记录两次调整间之差异，日后执行clock指令加上"--adjust"参数时，程序会自动根 据记录文件的数值差异，计算出平均值，自动调整硬件时钟的时间。
--debug 　详细显示指令执行过程，便于排错或了解程序执行的情形。
--directisa 　告诉clock指令不要通过/dev/rtc设备文件，直接对硬件时钟进行存取。这个参数适用于仅有ISA总线结构的老式电脑。
--getepoch 　把系统核心内的硬件时钟新时代数值，呈现到标准输出设备。
--hctosys 　Hardware Clock to System Time，把系统时间设成和硬件时钟一致。由于这个动作将会造成系统全面更新文件的存取时间，所以最好在系统启动时就执行它。
--set--date 　设置硬件时钟的日期和时间。
--setepoch--epoch=<年份> 　设置系统核心之硬件时钟的新时代数值，年份以四位树字表示。
--show 　读取硬件时钟的时间，并将其呈现至标准输出设备。
--systohc 　System Time to Hardware Clock，将系统时间存回硬件时钟内。
--test 　仅作测试，并不真的将时间写入硬件时钟或系统时间。
--utc 　把硬件时钟上的时间时为CUT，有时也称为UTC或UCT。
--version 　显示版本信息。
```
          
**常用命令：**
         
1. 获取当前的时间。
        
```bash
clock   # 获取当前的时间
```
          
2. 显示UTC时间。
         
```bash
clock -utc  # 显示utc时间
```
        
## 系统的重启，关机，注销等操作
### shutdown
>用来执行系统关机的命令。
           
shutdown命令用来系统关机命令。shutdown指令可以关闭所有程序，并依用户的需要，进行重新开机或关机的动作。
          
**语法：**
        
```html
shutdown(选项)(参数)
```
        
**选项：**
          
```html
-c：当执行“shutdown -h 11:50”指令时，只要按+键就可以中断关机的指令；
-f：重新启动时不执行fsck；
-F：重新启动时执行fsck；
-h：将系统关机；
-k：只是送出信息给所有用户，但不会实际关机；
-n：不调用init程序进行关机，而由shutdown自己进行；
-r：shutdown之后重新启动；
-t<秒数>：送出警告信息和删除信息之间要延迟多少秒。
```
        
**常用命令：**
       
1. 指定现在立即关机。
           
```bash
shutdown -h now
```
            
2. 指定5分钟后关机，同时送出警告信息给登入用户。
          
```bash
shutdown +5 "System will shutdown after 5 minutes"
```
          
### init
>init进程是所有Linux进程的父进程。
         
init命令是Linux下的进程初始化工具，init进程是所有Linux进程的父进程，它的进程号为1。init命令是Linux操作系统中不可缺少的程序之一，init进程是Linux内核引导运行的，是系统中的第一个进程。
        
**语法：**
         
```html
init(选项)(参数)
```
         
**选项：**
        
```html
-b:不执行相关脚本而直接进入单用户模式；
-s：切换到单用户模式。
```
        
**参数：**
         
运行等级：指定Linux系统要切换到的运行等级。
           
**常用命令：**
        
1. 查看系统进程命令。
        
```bash
root@001:~# ps -ef | head
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Nov24 ?        00:00:03 /lib/systemd/systemd --system --deserialize 24
root         2     0  0 Nov24 ?        00:00:00 [kthreadd]
root         4     2  0 Nov24 ?        00:00:00 [kworker/0:0H]
root         6     2  0 Nov24 ?        00:00:00 [mm_percpu_wq]
root         7     2  0 Nov24 ?        00:00:04 [ksoftirqd/0]
root         8     2  0 Nov24 ?        00:00:06 [rcu_sched]
root         9     2  0 Nov24 ?        00:00:00 [rcu_bh]
root        10     2  0 Nov24 ?        00:00:00 [migration/0]
root        11     2  0 Nov24 ?        00:00:01 [watchdog/0]
```
         
2. 查看系统当前运行的级别。
        
```bash
root@001:~# runlevel
N 5
```
          
**运行级别：**
            
运行级：简单地说，运行级就是操作系统当前正在运行的功能级别。这个级别从0到6，具有不同的功能。
        
```bash
#0  停机（千万不能把initdefault 设置为0）
#1  单用户模式
#2  多用户，没有 NFS(和级别3相似，会停止部分服务)
#3  完全多用户模式
#4  没有用到
#5  x11(Xwindow)
#6  重新启动（千万不要把initdefault 设置为6）
```
         
### reboot
>重新启动正在运行的Linux操作系统。
            
reboot命令用来重新启动正在运行的Linux操作系统。
         
**语法：**
             
```html
reboot(选项)
```
         
**选项：**
         
```html
-d：重新开机时不把数据写入记录文件/var/tmp/wtmp
-f：强制重新开机，不调用shutdown指令的功能
-i：在重新开机之前，先关闭所有网络界面
-n：重新开机之前不检查是否有未结束的程序
-w：仅做测试，并不真正将系统重新开机，只会把重开机的数据写入/var/log目录下的wtmp记录文件。
```
           
**常用命令：**
           
```bash
reboot   # 重开机
reboot -w   # 做个重开机的模拟（只有记录并不会真的重开机）
```
        
### halt
>关闭正在运行的Linux操作系统。
          
halt命令用来关闭正在运行的Linux操作系统。halt命令会先检测系统的runlevel，若runlevel为0或6，则关闭系统，否则即调用shutdown来关闭系统。
         
**语法：**
           
```html
halt(选项)
```
         
**选项：**
        
```html
-d：不要在wtmp中记录；
-f：不论目前的runlevel如何，不调用shutdown即强制关闭系统；
-i：在halt之前，关闭全部的网络界面；
-n：halt之前，不用先执行sync；
-p：halt之后，执行poweroff；
-w：仅在wtmp中记录，而不实际结束系统。
```
           
**常用命令：**
          
```bash
halt -p   # 关闭系统之后关闭电源
halt -d   # 关闭系统，但不留下记录
```
         
### poweroff
>关闭Linux系统，关闭记录会被写入到/var/log/wtmp日志文件中
            
poweroff命令会发送一个 ACPI 信号来通知系统关机。
          
**语法：**
         
```html
poweroff [选项]
```
         
**选项：**
          
```html
-n：关闭操作系统时不执行sync操作；
-w：不真正关闭操作系统，仅在日志文件“/var/log/wtmp”中；
-d：关闭操作系统时，不将操作写入日志文件“/var/log/wtmp”中添加相应的记录；
-f：强制关闭操作系统；
-i：关闭操作系统之前关闭所有的网络接口；
-h：关闭操作系统之前将系统中所有的硬件设置为备用模式。
```
         
**常用命令：**
         
1. 关闭Linux系统。
         
```bash
[root@localhost ~]# poweroff
```
         
### login
>登录系统或切换用户身份。
         
login命令用于给出登录界面，可用于重新登录或者切换用户身份，也可通过它的功能随时更换登入身份。在Slackware发行版中，您可在命令后面附加欲登入的用户名称，它会直接询问密码，等待用户输入。当/etc/nologin文件存在时，系统只允许root账号登入系统，其他用户一律不准登入。
          
**语法：**
       
```html
login(选项)(参数)
```
          
**选项：**
        
```html
-p：告诉login指令不销毁环境变量
-h：指定远程服务器的主机名
```
          
**参数：**
         
用户名：指定登录使用的用户名。
         
**常用命令：**
       
使用新的身份登录系统。
        
```bash
# login
```
              
### logout
>退出当前登录的Shell
        
logout命令用于退出当前登录的Shell，logout指令让用户退出系统，其功能和login指令相呼应。
         
**语法：**
         
```html
logout
```

**常用命令：**
              
退出系统：       
          
```bash
[root@runoob.com ~]# logout
```
         
## 文件和目录
### cd
>切换用户当前工作目录。
            
**语法：**
          
```html
cd [-L|[-P [-e]]] [dir]
```
          
**主要用途：**
            
- 切换工作目录至dir。其中dir的表示法可以是绝对路径或相对路径。
- 若参数dir省略，则默认为使用者的shell变量HOME。
- 如果dir指定为`~`时表示为使用者的shell变量HOME，`.`表示当前目录，`..`表示当前目录的上一级目录。
- 环境变量CDPATH是由冒号分割的一到多个目录，你可以将厂区的目录的上一级加入到CDPATH以便方便访问它们；如果dir以`/`开头那么CDPATH不会被使用。
- 当shopt选项cdable_vars打开时，如果dir在CDPATH及当前目录下均不存在，那么会把它当作环境变量，读取它的值作为要进入的目录。
          
**参数：**
         
dir(可选)：指定要切换到的目录。
         
**选项：**
         
```html
-L （默认值）如果要切换到的目标目录是一个符号连接，那么切换到符号连接的目录。
-P 如果要切换到的目标目录是一个符号连接，那么切换到它指向的物理位置目录。
-  当前工作目录将被切换到环境变量OLDPWD所表示的目录，也就是前一个工作目录。
```
           
**返回值：**
         
返回状态为成功除非无法进入指定的目录。
           
**常用命令：**
          
```bash
cd    # 进入用户主目录；
cd /  # 进入根目录
cd ~  # 进入用户主目录；
cd ..  # 返回上级目录（若当前目录为“/“，则执行完后还在“/"；".."为上级目录的意思）；
cd ../..  # 返回上两级目录；
cd !$  # 把上个命令的参数作为cd参数使用。
```
          
切换到上一个工作目录。
           
```bash
cd -
# 命令会首先显示要切换到的目标目录，然后再进入。
cd ${OLDPWD}
# 命令会直接切换到上一个工作目录。
```
           
关于CDPATH。
          
```bash
# 设置桌面文件夹作为CDPATH的值。
CDPATH='~/Desktop'
# 假设我们接下来要演示涉及到的路径~和~/Desktop下没有test3文件夹，现在新建它们。
mkdir ~/test3
mkdir ~/Desktop/test3
# 进入~目录。
cd ~
# 进入test3目录。
cd test3
# 执行后显示~/Desktop/test3并进入该目录，而不是~目录的test3目录。
# 如果CDPATH存在值，那么优先在CDPATH中查找并进入第一个匹配成功的，如果全部失败那么最后尝试当前目录。
```
             
关于cdable_vars。
           
```bash
# 打开选项。
shopt -s cdable_vars
# 假设当前路径以及CDPATH没有名为new_var的目录。
new_var='~/Desktop'
# 尝试进入。
cd new_var
# 关闭选项。
shopt -u cdable_vars
```
           
**注意：**
           
1. 该命令是bash内建命令，相关的帮助信息请查看help命令。
               
2. 建议您在编写脚本的过程中如有必要使用cd命令时，请增加必要的注释以用于提醒阅读者当前工作目录，以免出现诸如找不到文件这类问题的发生。
          
### pwd
>显示当前工作目录。
          
**目录：**
         
- bash内建命令
- GNU coreutils中的命令
       
#### **内建命令：**
        
**概要：**
      
```html
pwd [-LP]
```
         
**主要命令：**
        
- 显示当前工作目录。
       
**选项：**
       
```html
-L:（默认值）打印环境变量“$PWD”的值，可能为符号链接
-P：打印当前工作目录的物理位置
```
          
**返回值：**
           
返回状态为成功除非给出了非法选项或是当前目录无法读取。
         
**注意：**
        
1. 该命令是bash内建命令，相关的帮助信息请查看help命令。

            
#### **外部命令**
          
**概要：**
       
```html
pwd [OPTION]...
```
         
**主要用途：**
       
- 显示当前工作目录。
          
**选项：**
       
```html
-L, --logical 打印环境变量"$PWD"的值，可能为符号链接。
-P, --physical （默认值）打印当前工作目录的物理位置。
--help 显示帮助信息并退出。
--version 显示版本信息并退出。
```
           
**返回值：**
        
返回状态为成功除非给出了非法选项或是当前目录无法读取。
           
**注意：**
         
1. 该命令是GNU coreutils包中的命令，相关的帮助信息请查看man pwd或info coreutils 'pwd invocation'。
2. 启动或关闭内建命令请查看enable命令，关于同名优先级的问题请查看builtin命令的例子部分的相关讨论。
3. 在不禁用内建且当前环境没有定义pwd函数的情况下，使用/usr/bin/pwd指向coreutils的pwd，使用pwd指向bash内建的pwd。
           
### ls
>显示目录内容列表。
          
ls命令用来显示目标列表，在Linux中是使用率较高的命令。ls命令的输出信息可以进行彩色加亮显示，以区分不同类型的文件。
          
**语法：**
        
```html
ls [选项] [文件名...]
   [-1abcdfgiklmnopqrstuxABCDFGLNQRSUX] [-w cols] [-T cols] [-I pattern] [--full-time] 
   [--format={long,verbose,commas,across,vertical,single-col‐umn}] 
   [--sort={none,time,size,extension}] [--time={atime,access,use,ctime,status}] 
   [--color[={none,auto,always}]] [--help] [--version] [--]
```
        
**选项：**
         
```html
-C     # 多列输出，纵向排序。
-F     # 每个目录名加 "/" 后缀，每个 FIFO 名加 "|" 后缀， 每个可运行名加“ * ”后缀。
-R     # 递归列出遇到的子目录。
-a     # 列出所有文件，包括以 "." 开头的隐含文件。
-c     # 使用“状态改变时间”代替“文件修改时间”为依据来排序（使用“-t”选项时）或列出（使用“-l”选项时）。
-d     # 将目录名象其它文件一样列出，而不是列出它们的内容。
-i     # 输出文件前先输出文件系列号（即 i 节点号: i-node number）。 -l  列出（以单列格式）文件模式（file mode），文件的链     接数，所有者名，组名，文件大小（以字节为单位），时间信息，及文件名。缺省时，时间信息显示最近修改时间；可以以选项“-c”和“-u”选择显示其它两种时间信息。对于设    备文件，原先显示文件大小的区域通常显示的是主要和次要的号（majorand minor device numbers）。
-q     # 将文件名中的非打印字符输出为问号。（对于到终端的输出这是缺省的。）
-r     # 逆序排列。
-t     # 按时间信息排序。
-u     # 使用最近访问时间代替最近修改时间为依据来排序（使用“-t”选项时）或列出（使用“-l”选项时）。
-1     # 单列输出。
-1, --format=single-column  # 一行输出一个文件（单列输出）。如标准输出不是到终端，此选项就是缺省选项。
-a, --all # 列出目录中所有文件，包括以“.”开头的文件。
-b, --escape # 把文件名中不可输出的字符用反斜杠加字符编号(就象在 C 语言里一样)的形式列出。
-c, --time=ctime, --time=status
      # 按文件状态改变时间（i节点中的ctime）排序并输出目录内
      # 容。如采用长格式输出（选项“-l”），使用文件的状态改
      # 变时间取代文件修改时间。【译注：所谓文件状态改变（i节
      # 点中以ctime标志），既包括文件被修改，又包括文件属性（ 如所有者、组、链接数等等）的变化】
-d, --directory
      # 将目录名象其它文件一样列出，而不是列出它们的内容。
-f    #  不排序目录内容；按它们在磁盘上存储的顺序列出。同时启 动“ -a ”选项，如果在“ -f ”之前存在“ -l
      # ”、“ - -color ”或“ -s ”，则禁止它们。
-g    # 忽略，为兼容UNIX用。
-i, --inode
      # 在每个文件左边打印  i  节点号（也叫文件序列号和索引号:  file  serial  number and index num‐
      # ber）。i节点号在每个特定的文件系统中是唯一的。
-k, --kilobytes
      # 如列出文件大小，则以千字节KB为单位。
-l, --format=long, --format=verbose
      # 除每个文件名外，增加显示文件类型、权限、硬链接数、所       有者名、组名、大小（        byte
      # ）、及时间信息（如未指明是      其它时间即指修改时间）。对于6个月以上的文件或超出未来     1
      # 小时的文件，时间信息中的时分将被年代取代。
      # 每个目录列出前，有一行“总块数”显示目录下全部文件所       占的磁盘空间。块默认是        1024
      # 字节；如果设置了   POSIXLY_CORRECT  的环境变量，除非用“  -k  ”选项，则默认块大小是  512  字
      # 节。每一个硬链接都计入总块数（因此可能重复计数），这无 疑是个缺点。

# 列出的权限类似于以符号表示（文件）模式的规范。但是 ls
      # 在每套权限的第三个字符中结合了多位（ multiple bits ） 的信息，如下： s 如果设置了  setuid
      # 位或 setgid   位，而且也设置了相应的可执行位。 S 如果设置了 setuid 位或 setgid
      # 位，但是没有设置相应的可执行位。 t 如果设置了  sticky  位，而且也设置了相应的可执行位。  T
      # 如果设置了 sticky 位，但是没有设置相应的可执行位。              x
      # 如果仅仅设置了可执行位而非以上四种情况。 - 其它情况（即可执行位未设置）。
-m, --format=commas
      # 水平列出文件，每行尽可能多，相互用逗号和一个空格分隔。
-n, --numeric-uid-gid
      # 列出数字化的 UID 和 GID 而不是用户名和组名。
-o    #  以长格式列出目录内容，但是不显示组信息。等于使用“         --format=long          --no-group
      # ”选项。提供此选项是为了与其它版本的 ls 兼容。
-p    #  在每个文件名后附上一个字符以说明该文件的类型。类似“ -F ”选项但是不 标示可执行文件。
-q, --hide-control-chars
      # 用问号代替文件名中非打印的字符。这是缺省选项。
-r, --reverse
      # 逆序排列目录内容。
-s, --size
      # 在每个文件名左侧输出该文件的大小，以    1024   字节的块为单位。如果设置了   POSIXLY_CORRECT
      # 的环境变量，除非用“ -k ”选项，块大小是 512 字节。
-t, --sort=time
      # 按文件最近修改时间（ i 节点中的 mtime ）而不是按文件名字典序排序，新文件 靠前。
-u, --time=atime, --time=access, --time=use
      # 类似选项“    -t    ”，但是用文件最近访问时间（    i     节点中的     atime     ）取代文件修
      # 改时间。如果使用长格式列出，打印的时间是最近访问时间。
-w, --width cols
       # 假定屏幕宽度是      cols      （      cols     以实际数字取代）列。如未用此选项，缺省值是这
       # 样获得的：如可能先尝试取自终端驱动，否则尝试取自环境变量          COLUMNS          （如果设
       # 置了的话），都不行则取 80 。

-x, --format=across, --format=horizontal
       # 多列输出，横向排序。

-A, --almost-all
       # 显示除 "." 和 ".." 外的所有文件。

-B, --ignore-backups
       # 不输出以“ ~ ”结尾的备份文件，除非已经在命令行中给出。

-C, --format=vertical
       # 多列输出，纵向排序。当标准输出是终端时这是缺省项。使用命令名 dir 和 d 时， 则总是缺省的。

-D, --dired
       # 当采用长格式（“-l”选项）输出时，在主要输出后，额外打印一行：  //DIRED//  BEG1 END1 BEG2
       # END2 ...

# BEGn 和 ENDn 是无符号整数，记录每个文件名的起始、结束位置在输出中的位置（
#        字节偏移量）。这使得          Emacs          易于找到文件名，即使文件名包含空格或换行等非正
#        常字符也无需特异的搜索。
# 
# 如果目录是递归列出的（“ -R ”选项），每个子目录后列出类似一行：
       # //SUBDIRED//  BEG1 END1 ...  【译注：我测试了 TurboLinux4.0 和 RedHat6.1 ，发现它们都是在 “
       # //DIRED//     BEG1...     ”之后列出“     //SUBDIRED//     BEG1     ...      ”，也即只有一个
       # 而不是在每个子目录后都有。而且“ //SUBDIRED// BEG1 ... ”列出的是各个子目 录名的偏移。】

-F, --classify, --file-type
       # 在每个文件名后附上一个字符以说明该文件的类型。“  * ”表示普通的可执行文件； “ / ”表示目录；“
       # @ ”表示符号链接；“ | ”表示FIFOs；“ = ”表示套接字 (sockets) ；什么也没有则表示普通文件。

-G, --no-group
       # 以长格式列目录时不显示组信息。

-I, --ignorepattern
       # 除非在命令行中给定，不要列出匹配shell文件名匹配式（pattern ，不是指一般
       # 表达式）的文件。在shell中，文件名以"."起始的不与在文件名匹配式(pattern)
       # 开头的通配符匹配。

-L, --dereference
       # 列出符号链接指向的文件的信息，而不是符号链接本身。

-N, --literal
       # 不要用引号引起文件名。

-Q, --quote-name
       # 用双引号引起文件名，非打印字符以 C 语言的方法表示。

-R, --recursive
       # 递归列出全部目录的内容。

-S, --sort=size
       # 按文件大小而不是字典序排序目录内容，大文件靠前。

-T, --tabsize cols
       # 假定每个制表符宽度是 cols 。缺省为 8。为求效率， ls 可能在输出中使用制表符。  若 cols 为
       0，则不使用制表符。

-U, --sort=none
       # 不排序目录内容；按它们在磁盘上存储的顺序列出。（选项“-U”和“-f”的不
       # 同是前者不启动或禁止相关的选项。）这在列很大的目录时特别有用，因为不加排序
       # 能显著的加快速度。

-X, --sort=extension
       # 按文件扩展名（由最后的 "." 之后的字符组成）的字典序排序。没有扩展名的先列 出。

--color[=when]
       # 指定是否使用颜色区别文件类别。环境变量  LS_COLORS  指定使用的颜色。如何设置 这个变量见 dir‐
       # colors(1) 。 when 可以被省略，或是以下几项之一：
none # 不使用颜色，这是缺省项。
       # auto 仅当标准输出是终端时使用。 always 总是使用颜色。指定 --color 而且省略 when  时就等同于
       # --color=always 。

--full-time
       # 列出完整的时间，而不是使用标准的缩写。格式如同          date(1)          的缺省格式；此格式
       # 是不能改变的，但是你可以用 cut(1) 取出其中的日期字串并将结果送至命令 “ date -d ”。

# 输出的时间包括秒是非常有用的。（ Unix 文件系统储存文件的时间信息精确到秒，
       # 因此这个选项已经给出了系统所知的全部信息。）例如，当你有一个         Makefile          文件
       # 不能恰当的生成文件时，这个选项会提供帮助。
```
           
**参数：**
       
目录：指定要显示列表的目录，也可以是具体的文件。
          
**常用命令：**
         
1. 仅列出当前目录可见文件
          
```bash
$ ls   
```
          
2. 列出当前目录可见文件详细信息
          
```bash
$ ls -l 
```
         
3. 列出详细信息并以可读大小显示文件
            
```bash
$ ls -hl
```
           
4. 列出所有文件（包括隐藏）的详细信息
          
```bash
$ ls -al
```
         
5. 水平输出文件列表
         
```bash
root@002:~# root@002:~# ls -m
HostGuardAgent_Linux64_V1.12.39.deb.sha256, hostguard_setup_config.dat, HwAgentInstall_64.sh, swapfile, test, www
```
         
6. 输出长格式列表
        
```bash
root@002:~# ls -1
HostGuardAgent_Linux64_V1.12.39.deb.sha256
hostguard_setup_config.dat
HwAgentInstall_64.sh
swapfile
test
www
```
              
7. 最近修改的文件显示在最上面
         
```bash
root@002:~# ls -t
test  www  swapfile  HwAgentInstall_64.sh  HostGuardAgent_Linux64_V1.12.39.deb.sha256  hostguard_setup_config.dat
```
       
8. 显示递归文件
          
```bash
root@002:~# ls -R
.:
HostGuardAgent_Linux64_V1.12.39.deb.sha256  hostguard_setup_config.dat  HwAgentInstall_64.sh  swapfile  test  www

./test:

./www:
html  php  phpmyadmin  zzuli

./www/html:
docker-tensorflow  interview  main  resume

./www/html/docker-tensorflow:
docker-tensorflow.iml  favicon.ico  index.html  plug  style.css  test.md

./www/html/docker-tensorflow/plug:
editor.md-master
.
.
.
.
.
```
          
9. 打印文件的UID和GID
　　　　　　　　
```bash
root@002:~# ls -n
total 10485800
-rw-r--r-- 1 0 0         102 Aug  1 15:57 HostGuardAgent_Linux64_V1.12.39.deb.sha256
-rw-r--r-- 1 0 0        1540 Aug  1 15:57 hostguard_setup_config.dat
-rwxr-xr-x 1 0 0       18403 Aug  9 09:56 HwAgentInstall_64.sh
-rw-r--r-- 1 0 0 10737418240 Aug 23 16:49 swapfile
drwxr-xr-x 2 0 0        4096 Nov  5 12:18 test
drwxr-xr-x 6 0 0        4096 Oct 19 21:44 www
```
           
10. 按照特殊字符对文件进行分类
         
```bash
root@002:~# ls -F
HostGuardAgent_Linux64_V1.12.39.deb.sha256  hostguard_setup_config.dat  HwAgentInstall_64.sh*  swapfile  test/  www/
```
         
11. 列出文件并标记颜色分类
          
```bash
root@002:~# ls --color=auto
HostGuardAgent_Linux64_V1.12.39.deb.sha256  hostguard_setup_config.dat  HwAgentInstall_64.sh  swapfile  test  www
```
           
### tree
>树状图列出目录的内容。
          
tree命令以树状图列出目录的内容。
            
**语法：**
         
```html
tree(选项)(参数)
```
          
**选项：**
         
```html
------- 列表选项 -------
-a            # 显示所有文件和目录。
-d            # 先是目录名称而非文件。
-l            # 如遇到性质为符号连接的目录，直接列出该连接所指向的原始目录。
-f            # 在每个文件或目录之前，显示完整的相对路径名称。
-x            # 将范围局限在现行的文件系统中，若指定目录下的某些子目录，其存放于另一个文件系统上，则将该目录予以排除在寻找范围外。
-L level      # 限制目录显示层级。
-R            # Rerun tree when max dir level reached.
-P pattern    # <范本样式> 只显示符合范本样式的文件和目录名称。
-I pattern    # Do not list files that match the given pattern.
--ignore-case # Ignore case when pattern matching.
--matchdirs   # Include directory names in -P pattern matching.
--noreport    # Turn off file/directory count at end of tree listing.
--charset X   # Use charset X for terminal/HTML and indentation line output.
--filelimit # # Do not descend dirs with more than # files in them.
--timefmt <f> # Print and format time according to the format <f>.
-o filename   # Output to file instead of stdout.
-------- 文件选项 ---------
-q            # 用“？”号取代控制字符，列出文件和目录名称。
-N            # 直接列出文件和目录名称，包括控制字符。
-Q            # Quote filenames with double quotes.
-p            # 列出权限标示。
-u            # 列出文件或目录的拥有者名称，没有对应的名称时，则显示用户识别码。
-g            # 列出文件或目录的所属群组名称，没有对应的名称时，则显示群组识别码。
-s            # 列出文件和目录大小。
-h            # Print the size in a more human readable way.
--si          # Like -h, but use in SI units (powers of 1000).
-D            # 列出文件或目录的更改时间。
-F            # 在执行文件，目录，Socket，符号连接，管道名称名称，各自加上"*"，"/"，"@"，"|"号。
--inodes      # Print inode number of each file.
--device      # Print device ID number to which each file belongs.
------- 排序选项 -------
-v            # Sort files alphanumerically by version.
-t            # 用文件和目录的更改时间排序。
-c            # Sort files by last status change time.
-U            # Leave files unsorted.
-r            # Reverse the order of the sort.
--dirsfirst   # List directories before files (-U disables).
--sort X      # Select sort: name,version,size,mtime,ctime.
------- 图形选项 ------
-i            # 不以阶梯状列出文件和目录名称。
-A            # 使用ASNI绘图字符显示树状图而非以ASCII字符组合。
-S            # Print with CP437 (console) graphics indentation lines.
-n            # Turn colorization off always (-C overrides).
-C            # 在文件和目录清单加上色彩，便于区分各种类型。
------- XML / HTML / JSON选项 -------
-X            # Prints out an XML representation of the tree.
-J            # Prints out an JSON representation of the tree.
-H baseHREF   # Prints out HTML format with baseHREF as top directory.
-T string     # Replace the default HTML title and H1 header with string.
--nolinks     # Turn off hyperlinks in HTML output.
---- 杂项选项 ----
--version     # 输入版本信息。
--help        # 打印使用帮助信息。
--            # Options processing terminator.
```
         
**参数：**
           
目录：执行tree指令，它会列出指定目录下的所有文件，包括子目录里的文件。
            
**常用命令：**
        
1. 列出目录/www/第一级文件名。
       
```bash
root@002:~# tree www/ -L 1
www/
├── html
├── php
├── phpmyadmin
└── zzuli

4 directories, 0 files
```
         
### mkdir
>用来创建目录。
         
mkdir命令用来创建目录。该命令创建由dirname命令的目录。。如果在目录名的前面没有加任何路径名，则在当前目录下创建由dirname指定的目录；如果给出了一个已经存在的路径，将会在该目录下创建一个指定的目录。在创建目录时，应保证新建的目录与它所在目录下的文件没有重名。
         
**注意：**在创建文件时，不要把所有的文件都存放在主目录中，可以创建子目录，通过它们来更有效地组织文件。最好采用前后一致的命名方式来区分文件和目录。例如，目录名可以以大写字母开头，这样，在目录列表中就出现在前面。
          
在一个子目录中应包含类型相似或用途相近的文件。例如，应建立一个子目录，它包含所有的数据库文件，另有一个子目录应包含电子表格文件，还有一个子目录应包含文字处理文档，等等。目录也是文件，它们和普通文件一样遵循相同的命名规则，并且利用全路径可以唯一地指定一个目录。
          
**语法：**
        
```html
mkdir (选项)(参数)
```
        
**选项：**
         
```html
-Z：设置安全上下文，当使用SELinux时有效；
-m<目标属性>或--mode<目标属性>建立目录的同时设置目录的权限；
-p或--parents 若所要建立目录的上层目录目前尚未建立，则会一并建立上层目录；
--version 显示版本信息。
```
        
**参数：**
           
目录：指定要创建的目录列表，多个目录之间用空格隔开。
            
**常用命令：**
        
1. 在目录/usr/meng下建立子目录test，并且只有文件主有读、写和执行权限，其他人无权访问
           
```bash
mkdir -m 700 /usr/meng/test
```
          
2. 在当前目录中建立bin和bin下的os_1目录，权限设置为文件主可读、写、执行，同组用户可读和执行，其他用户无权访问
           
```bash
mkdir -p-m 750 bin/os_1
```
         
### rm
>用于删除给定的文件和目录
         
rm命令可以删除一个目录中的一个或多个文件或目录，也可以将某个目录及其下属的所有文件及其子目录均删除掉。对于链接文件，只是删除整个链接文件，而原有文件保持不变。
          
**语法：**
         
```html
rm (选项)(参数)
```
          
**选项：**
        
```html
-d：直接把欲删除的目录的硬连接数据删除成0，删除该目录；
-f：强制删除文件或目录；
-i：删除已有文件或目录之前先询问用户；
-r或-R：递归处理，将指定目录下的所有文件与子目录一并处理；
--preserve-root：不对根目录进行递归操作；
-v：显示指令的详细执行过程。
```
          
**参数：**
          
文件：指定被删除的文件列表，如果参数中含有目录，则必须加上-r或者-R选项。
            
**常用命令：**
          
1. 交互式删除当前目录下的文件test和example
            
```bash
rm -i test example
Remove test ?n（不删除文件test)
Remove example ?y（删除文件example)
```
          
2. 删除当前目录下除隐含文件外的所有文件和子目录。
        
```bash
# rm -r *      ## 谨慎操作
```
             
3. 删除文件。
            
```bash
# rm 文件1 文件2 ... 
```
                   
4. 删除目录。
             
```bash
## rm -r [目录名称] -r 表示递归地删除目录下的所有文件和目录。-f 表示强制删除

# rm -rf testdir
# rm -r tesrdir
```
             
5. 显示当前删除操作的详情
         
```bash
## rm -v [文件/目录]
root@001:~# rm -v test/
rm: cannot remove 'test/': Is a directory
```
                  
### mv
>用来对文件或目录重新命名。
           
mv命令用来对文件或目录重新命名，或者将文件从一个目录移到另一个目录中。source表示源文件或目录，target表示目标文件或目录。如果将一个文件移到一个已经存在的目标文件中，则目标文件的内容将被覆盖。
           
mv命令可以用来将源文件移至一个目标文件中，或将一组文件移至一个目标目录中。源文件被移至目标文件有两种不同的结果：
          
1. 如果目标文件是到某一目录文件的路径，源文件会被移到此目录下，且文件名不变。
         
2. 如果目标文件不是目录文件，则源文件名（只能有一个）会变为此目标文件名，并覆盖已存在的同名文件。如果源文件和目标文件在同一个目录下，mv的作用就是改文件名。当目标文件是目录文件时，源文件或目录参数可以有多个，则所有的源文件都会被移至目标文件中。所有移到该目录下的文件都将保留以前的文件名。
               
注意事项：mv与cp的结果不同，mv好像文件“搬家”，文件个数并未增加。而cp对文件进行复制，文件个数增加了。
           
**语法：**
         
```html
mv(选项)(参数)
```
              
**选项：**
            
```html
--backup=<备份模式>：若需覆盖文件，则覆盖前先行备份；
-b：当文件存在时，覆盖前，为其创建一个备份；
-f：若目标文件或目录与现有的文件或目录重复，则直接覆盖现有的文件或目录；
-i：交互式操作，覆盖前先行询问用户，如果源文件与目标文件或目标目录中的文件同名，则询问用户是否覆盖目标文件。用户输入”y”，表示将覆盖目标文件；输入”n”，表示取消对源文件的移动。这样可以避免误将文件覆盖。
--strip-trailing-slashes：删除源文件中的斜杠“/”；
-S<后缀>：为备份文件指定后缀，而不使用默认的后缀；
--target-directory=<目录>：指定源文件要移动到目标目录；
-u：当源文件比目标文件新或者目标文件不存在时，才执行移动操作。
```
              
**参数：**
         
- 源文件：源文件列表
- 目标文件：如果“目标文件”是文件名则在移动文件的同时，将其改名为“目标文件”；如果“目标文件”是目录名则将源文件移动到“目标文件”下。
          
**参数：**
        
- 源文件：源文件列表。
- 目标文件：如果“目标文件”是文件名则在移动文件的同时，将其改名为“目标文件”；如果“目标文件”是目录名则将源文件移动到“目标文件”下。
         
**常用命令：**
            
1. 将目录/usr/men中的所有文件移到当前目录（用.表示）中：
           
```bash
mv /usr/men/* .
```
           
2. 移动文件
          
```bash
mv file_1.txt /home/office/
```
           
3. 移动多个文件
        
```bash
mv file_2.txt file_3.txt file_4.txt /home/office/
mv *.txt /home/office/
```
          
4. 重命名文件或目录
       
```bash
mv file_1.txt file_2.txt # 将文件file_1.txt改名为file_2.txt
```
         
5. 重命名目录
         
```bash
mv directory_1/ directory_2/
```
            
6. 打印移动信息
         
```bash
mv -v *.txt /home/office
```

7. 提示是否覆盖文件
          
```bash
mv -i file_1.txt /home/office
```
        
8. 源文件比目标文件新时才执行更新
           
```bash
mv -uv *.txt /home/office
```
         
9. 不要覆盖任何已存在的文件
           
```bash
mv -vn *.txt /home/office
```
          
10. 复制时创建备份
          
```bash
mv -bv *.txt /home/office
```
          
11. 无条件覆盖已经存在的文件
          
```bash
mv -f *.txt /home/office
```
        
### cp
>将源文件或目录复制到目标文件或目录中。
             
cp命令用来将一个或多个源文件或者目录复制到指定的目的文件或目录。它可以将单个源文件复制成一个指定文件名的具体或一个已经存在的目录下。cp命令还支持同时复制多个文件，当一次复制多个文件时，目标文件参数必须是一个已经存在的目录，否则将出现错误。
            
**语法：**
           
```html
cp(选项)(参数)
```
          
**选项：**
         
```html
-a：此参数的效果和同时指定"-dpR"参数相同；
-d：当复制符号连接时，把目标文件或目录也建立为符号连接，并指向与源文件或目录连接的原始文件或目录；
-f：强行复制文件或目录，不论目标文件或目录是否已存在；
-i：覆盖既有文件之前先询问用户；
-l：对源文件建立硬连接，而非复制文件；
-p：保留源文件或目录的属性；
-R/r：递归处理，将指定目录下的所有文件与子目录一并处理；
-s：对源文件建立符号连接，而非复制文件；
-u：使用这项参数后只会在源文件的更改时间较目标文件更新时或是名称相互对应的目标文件并不存在时，才复制文件；
-S：在备份文件时，用指定的后缀“SUFFIX”代替文件的默认后缀；
-b：覆盖已存在的文件目标前将目标文件备份；
-v：详细显示命令执行的操作。
```
           
**参数：**
            
- 源文件：制定源文件列表。默认情况下，cp命令不能复制目录，如果要复制目录，则必须使用-R选项；
- 目标文件：指定目标文件。当“源文件”为多个文件时，要求“目标文件”为指定的目录。
          
**常用命令：**
         
1. 将指定文件复制到当前目录下。
          
```bash
cp ../mary/homework/assign .
```
            
2. 将文件file复制到目录/usr/men/tmp，并改名为file1。
         
```bash
cp file /usr/men/tmp/file1
```
           
3. 将目录/usr/men下的所有文件及其子目录复制到目录/usr/zh中。
         
```bash
cp -r /usr/men /usr/zh
```
              
4. 交互式地将目录/usr/men中的以m打头的所有.c文件复制到目录/usr/zh中。
          
```bash
cp -i /usr/men m*.c /usr/zh
```
         
5. 递归强制复制目录到指定目录中覆盖已存在文件。
         
```bash
cp -rfb ./* ../backup
# 将当前目录下所有文件，复制到当前目录的兄弟目录 backup 文件夹中
```
        
6. 拷贝目录下的隐藏文件如.babelrc。
         
```bash
cp -r aaa/.* ./bbb
# 将 aaa 目录下的，所有`.`开头的文件，复制到 bbb 目录中。

cp -a aaa ./bbb/ 
# 记住后面目录最好的'/' 带上 `-a` 参数
```
          
### ln
>用来为文件创建链接。
            
ln命令用来为文件创建链接，链接类型分为硬链接和符号链接两种，默认的链接类型是硬链接。如果要创建符号链接必须使用“-s”选项。
           
注意：符号链接文件不是一个独立的文件，它的许多属性依赖于源文件，所以给符号链接文件设置存取权限是没有意义的。
         
**语法：**
            
```html
ln [选项]... [-T] 目标 链接名    (第一种格式)
　或：ln [选项]... 目标        (第二种格式)
　或：ln [选项]... 目标... 目录    (第三种格式)
　或：ln [选项]... -t 目录 目标...    (第四种格式)
```
        
**选项：**
           
```html
    --backup[=CONTROL]  为每个已存在的目标文件创建备份文件
-b        类似--backup，但不接受任何参数
-d, -F, --directory   创建指向目录的硬链接(只适用于超级用户)
-f, --force     强行删除任何已存在的目标文件
-i, --interactive           覆盖既有文件之前先询问用户；
-L, --logical               取消引用作为符号链接的目标
-n, --no-dereference        把符号链接的目的目录视为一般文件；
-P, --physical              直接将硬链接到符号链接
-r, --relative              创建相对于链接位置的符号链接
-s, --symbolic              对源文件建立符号链接，而非硬链接；
-S, --suffix=SUFFIX         用"-b"参数备份目标文件后，备份文件的字尾会被加上一个备份字符串，预设的备份字符串是符号“~”，用户可通过“-S”参数来改变它；
-t, --target-directory=DIRECTORY  指定要在其中创建链接的DIRECTORY
-T, --no-target-directory   将“LINK_NAME”视为常规文件
-v, --verbose               打印每个链接文件的名称
    --help    显示此帮助信息并退出
    --version   显示版本信息并退出
```
         
**参数：**
          
- 源文件：指定链接的源文件。如果使用-s选项创建符号链接，则“源文件”可以是文件或者目录。创建硬链接时，则“源文件”参数只能是文件；
- 目标文件：指定源文件的目标链接文件。
             
```html
none, off       # 不进行备份(即使使用了--backup 选项)
numbered, t     # 备份文件加上数字进行排序
existing, nil   # 若有数字的备份文件已经存在则使用数字，否则使用普通方式备份
simple, never   # 永远使用普通方式备份
```
            
**常用命令：**
            
1. 将目录/usr/mengqc/mub1下的文件m2.c链接到目录/usr/liu下的文件a2.c。
            
```bash
cd /usr/mengqc
ln /mub1/m2.c /usr/liu/a2.c
```
           
在执行ln命令之前，目录/usr/liu中不存在a2.c文件。执行ln之后，在/usr/liu目录中才有a2.c这一项，表明m2.c和a2.c链接起来（注意，二者在物理上是同一文件），利用ls -l命令可以看到链接数的变化。
          
2. 在目录/usr/liu下建立一个符号链接文件abc，使它指向目录/usr/mengqc/mub1。
          
```bash
ln -s /usr/mengqc/mub1 /usr/liu/abc
```
           
执行该命令后，/usr/mengqc/mub1代表的路径将存放在名为/usr/liu/abc的文件中。
               
**扩展知识：**
           
Linux具有为一个文件起多个名字的功能，称为链接。被链接的文件可以存放在相同的目录下，但是必须有不同的文件名，而不用在硬盘上为同样的数据重复备份。另外，被链接的文件也可以有相同的文件名，但是存放在不同的目录下，这样只要对一个目录下的该文件进行修改，就可以完成对所有目录下同名链接文件的修改。对于某个文件的各链接文件，我们可以给它们指定不同的存取权限，以控制对信息的共享和增强安全性。
            
文件链接有两种形式，即硬链接和符号链接。
               
**硬链接**
           
建立硬链接时，在另外的目录或本目录中增加目标文件的一个目录项，这样，一个文件就登记在多个目录中。如图所示的m2.c文件就在目录mub1和liu中都建立了目录项。
             
创建硬链接后，己经存在的文件的I节点号（Inode）会被多个目录文件项使用。一个文件的硬链接数可以在目录的长列表格式的第二列中看到，无额外链接的文件的链接数为l。
                 
在默认情况下，ln命令创建硬链接。ln命令会增加链接数，rm命令会减少链接数。一个文件除非链接数为0，否则不会从文件系统中被物理地删除。
             
对硬链接有如下限制：
                 
- 不能对目录文件做硬链接。
- 不能在不同的文件系统之间做硬链接。就是说，链接文件和被链接文件必须位于同一个文件系统中。
            
**符号链接**
            
符号链接也称为软链接，是将一个路径名链接到一个文件。这些文件是一种特别类型的文件。事实上，它只是一个文本文件（如图中的abc文件），其中包含它提供链接的另一个文件的路径名，如图中虚线箭头所示。另一个文件是实际包含所有数据的文件。所有读、写文件内容的命令被用于符号链接时，将沿着链接方向前进来访问实际的文件。
              
!符号连接
           
与硬链接不同的是，符号链接确实是一个新文件，当然它具有不同的I节点号；而硬链接并没有建立新文件。
                
符号链接没有硬链接的限制，可以对目录文件做符号链接，也可以在不同文件系统之间做符号链接。
           
用ln -s命令建立符号链接时，源文件最好用绝对路径名。这样可以在任何工作目录下进行符号链接。而当源文件用相对路径时，如果当前的工作路径与要创建的符号链接文件所在路径不同，就不能进行链接。
               
符号链接保持了链接与源文件或目录之间的区别：
           
- 删除源文件或目录，只删除了数据，不会删除链接。一旦以同样文件名创建了源文件，链接将继续指向该文件的新数据。
- 在目录长列表中，符号链接作为一种特殊的文件类型显示出来，其第一个字母是l。
- 符号链接的大小是其链接文件的路径名中的字节数。
- 当用ln -s命令列出文件时，可以看到符号链接名后有一个箭头指向源文件或目录，例如lrwxrwxrwx … 14 jun 20 10:20 /etc/motd->/original_file其中，表示“文件大小”的数字“14”恰好说明源文件名original_file由14个字符构成。