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