# java 基础知识
## 简介及相关知识
### Java语言介绍以及优势
ava是由Sun Microsystems公司于1995年5月推出的Java面向对象程序设计语言和Java平台的总称。由James Gosling和同事们共同研发，并在1995年正式推出。
        
Java分为三个体系：
- JavaSE（J2SE）（Java2 Platform Standard Edition，java平台标准版）
- JavaEE(J2EE)(Java 2 Platform,Enterprise Edition，java平台企业版)
- JavaME(J2ME)(Java 2 Platform Micro Edition，java平台微型版)。
          
2005年6月，JavaOne大会召开，SUN公司公开Java SE 6。此时，Java的各种版本已经更名以取消其中的数字"2"：J2EE更名为Java EE, J2SE更名为Java SE，J2ME更名为Java ME。
       
#### 主要优势
- Java语言是简单的
Java语言的语法与C语言和C++语言很接近，使得大多数程序员很容易学习和使用。另一方面，Java丢弃了C++中很少使用的、很难理解的、令人迷惑的那些特性，如操作符重载、多继承、自动的强制类型转换。特别地，Java语言不使用指针，而是引用。并提供了自动的废料收集，使得程序员不必为内存管理而担忧。

- Java语言是面向对象的
Java语言提供类、接口和继承等原语，为了简单起见，只支持类之间的单继承，但支持接口之间的多继承，并支持类与接口之间的实现机制（关键字为implements）。Java语言全面支持动态绑定，而C++语言只对虚函数使用动态绑定。总之，Java语言是一个纯的面向对象程序设计语言。
      
- Java语言是分布式的
Java语言支持internet应用的开发，在基本的Java应用编程接口中有一个网络应用编程接口（Java net），它提供了用于网络应用编程的类库，包括URL、URLConnection、Socket、ServerSocket等。Java的RMI（远程方法激活）机制也是开发分布式应用的重要手段。
     
- Java语言是健壮的
Java的强类型机制、异常处理、垃圾的自动收集等是Java程序健壮性的重要保证。对指针的丢弃是Java的明智选择。Java的安全检查机制使得Java更具健壮性。
       
- Java语言是安全的
Java通常被用在网络环境中，为此，Java提供了一个安全机制以防恶意代码的攻击。除了Java语言具有的许多安全特性以外，Java对通过网络下载的类具有一个安全防范机制（类ClassLoader），如分配不同的名字空间以防替代本地的同名类、字节代码检查，并提供安全管理机制（类SecurityManager）让Java应用设置安全哨兵。
         
- Java语言是体系结构中立的
Java程序（后缀为Java的文件）在Java平台上被编译为体系结构中立的字节码格式（后缀为class的文件），然后可以在实现这个Java平台的任何系统中运行。这种途径适合与异构的网络环境和软件的分发。
       
- Java语言是可移植的
这种可移植性来源于体系结构中立性，另外，Java还严格规定了各个基本数据类型的长度。Java系统本身也具有很强的可移植性，Java编译器是用Java实现的，Java的运行环境是用ANSI C实现的。
         
- Java语言是解释型的
如前所述，Java程序在Java平台上被编译为字节码格式，然后可以在实现这个Java平台的任何系统中运行。在运行时，Java平台中的Java解释器对这些字节码进行解释执行，执行过程中需要的类在联接阶段被载入到运行环境中。
     
- Java是高性能的
与那些解释型的高级脚本语言相比，Java的确是高性能的。事实上，Java的运行速度随着JIT（Just-In-Time）编译器技术的发展越来越接近与C++。
       
- Java语言是多线程的
在Java语言中，线程是一种特殊的对象，它必须由Thread类或其子（孙）类来创建。通常有两种方法来创建线程：其一，使用型构为Thread(Runnable)的构造子将一个实现了Runnable接口的对象包装成一个线程，其二，从Thread类派生出子类并重写run方法，使用该子类创建的对象即为线程。值得注意的是Thread类已经实现了Runnable接口，因此，任何一个线程均有它的run方法，而run方法中包含了线程所要运行的代码。线程的活动由一组方法来控制。Java语言支持多个线程的同时执行，并提供多线程之间的同步机制（关键字为synchronized）。
        
- Java语言是动态的
Java语言的设计目标之一是适应于动态变化的环境。Java程序需要的类能够动态地被载入到运行环境，也可以通过网络来载入所需要的类。这也有利于软件的升级。另外，Java中的类有一个运行时刻的表示，能进行运行时刻的类型检查。
           
## JDK和JRE和JVM
### Java中JDK和JRE的区别
JRE是Java Runtime Environment的缩写，是Java程序的运行环境。
       
既然是运行，当然要包含jvm，也就是大家熟悉的虚拟机，还有所有Java类库的class文件，都在lib目录下打包成jar。
       
JDK是Java Development Kit的缩写，是Java的开发工具包。
     
主要包含了各种类库和工具，当然也包含了另外一个JRE，那么为什么要包含另外一个JRE呢？而且在JDK安装目录/JRE/bin目录下，包含有server一个文件夹包含一个jvm.dll，这说明JDK提供了一个虚拟机。另外，JDK的bin目录下有各种Java程序需要用到的命令，与JRE的bin目录最明显的区别就是JDK文件下才有javac，这一点很好理解，因为JRE只是一个运行环境而已，与开发无关。正因为如此，具备开发功能的JDK所包含的JRE下才会同时有server的JVM，而仅仅作为运行环境的JRE下，只需要server的jvm.dll就够了。注意：JDK所提供的运行环境和工具需要进行环境变量的配置以后才能使用。     
JDK是Java的开发工具，它不仅提供了Java程序运行所需的JRE，还提供了一系列的编译、运行等工具，如javac、java、javaw等。JRE只是Java程序的运行环境。它最核心的内容就是JVM（Java虚拟机）及核心类库。

### JDK和JRE的区别
通俗点来说：JDK是Java的开发包，其中包括JRE；JRE仅仅是Java的运行时环境；而JDK包括了同版本的JRE，此外还包括有编译器和其他工具。

### 为什么Sun要让JDK安装两套相同的JRE？
这是因为JDK里面有很多用Java所编写的开发工具（如javac.exe、jar.exe等），而且都放置在 \lib\tools.jar 里。从下面例子可以看出，先将tools.jar改名为tools1.jar，然后运行javac.exe，显示如下结果： Exception in thread "main" java.lang.NoClassDefFoundError: com/sun/tools/javac /Main 这个意思是说，你输入javac.exe与输入 java -cp c:\jdk\lib\tools.jar com.sun.tools.javac.Main 是一样的，会得到相同的结果。从这里我们可以证明javac.exe只是一个包装器（Wrapper），而制作的目的是为了让开发者免于输入太长的指令。而且可以发现\lib目录下的程序都很小，不大于2 9K，从这里我们可以得出一个结论。就是JDK里的工具几乎是用Java所编写，所以也是Java应用程序，因此要使用JDK所附的工具来开发Java程序，也必须要自行附一套JRE才行，所以位于C:\Program Files\Java目录下的那套JRE就是用来运行一般Java程序用的。
       
### 如果一台电脑安装两套以上的JRE，谁来决定呢？
这个重大任务就落在java.exe身上。Java.exe的工作就是找到合适的JRE来运行Java程序。 Java.exe依照底下的顺序来查找JRE：自己的目录下有没有JRE；父目录有没有JRE；查询注册表： [HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft\Java Runtime Environment] 所以java.exe的运行结果与你的电脑里面哪个JRE被执行有很大的关系。

### JDK简介
JDK : Java Development ToolKit(Java开发工具包)。JDK是整个JAVA的核心，包括了Java运行环境（Java Runtime Envirnment），一堆Java工具（javac/java/jdb等）和Java基础的类库（即Java API 包括rt.jar）。
        
JDK是java开发工具包，在其安装目录下面有六个文件夹、一些描述文件、一个src压缩文件。bin、include、lib、 jre这四个文件夹起作用，demo、sample是一些例子。可以看出来JDK包含JRE，而JRE包含JVM。
bin:最主要的是编译器(javac.exe)
include:java和JVM交互用的头文件
lib：类库
jre:java运行环境（注意：这里的bin、lib文件夹和jre里的bin、lib是不同的）
总的来说JDK是用于java程序的开发,而jre则是只能运行class而没有编译的功能。 
JDK是提供给Java开发人员使用的，其中包含了java的开发工具，也包括了JRE。所以安装了JDK，就不用在单独安装JRE了。 其中的开发工具包括编译工具(javac.exe)打包工具(jar.exe)等

在JDK的安装目录下有一个jre目录，里面有两个文件夹bin和lib，在这里可以认为bin里的就是jvm，lib中则是jvm工作所需要的类库，而jvm和 lib合起来就称为jre。
       
### JDK版本
JDK是整个JAVA的核心，包括了Java运行环境JRE（Java Runtime Envirnment）、一堆Java工具（javac/java/jdb等）和Java基础的类库（即Java API 包括rt.jar）。
①SE(J2SE)，standard edition，标准版，是我们通常用的一个版本，从JDK 5.0开始，改名为Java SE。
②EE(J2EE)，enterprise edition，企业版，使用这种JDK开发J2EE应用程序，从JDK 5.0开始，改名为Java EE。
③ME(J2ME)，micro edition，主要用于移动设备、嵌入式设备上的java应用程序，从JDK 5.0开始，改名为Java ME。
         
我们常常用JDK来代指Java API，Java API是Java的应用程序接口，其实就是前辈们写好的一些java Class，包括一些重要的语言结构以及基本图形，网络和文件I/O等等 ，我们在自己的程序中，调用前辈们写好的这些Class，来作为我们自己开发的一个基础。当然，现在已经有越来越多的性能更好或者功能更强大的第三方类库供我们使用。

### JRE简介
JRE(Java Runtime Environment,Java运行环境)，包含JVM标准实现及Java核心类库。JRE是Java运行环境，并不是一个开发环境，所以没有包含任何开发工具（如编译器和调试器）。      
JRE是运行基于Java语言编写的程序所不可缺少的运行环境。也就是通过它，Java的开发者才得以将自己开发的程序发布到用户手中，让用户使用。          
JRE中包含了Java virtual machine（JVM），runtime class libraries和Java application launcher，这些是运行Java程序的必要组件。与大家熟知的JDK不同，JRE是Java运行环境，并不是一个开发环境，所以没有包含任何开发工具（如编译器和调试器），只是针对于使用Java程序的用户。
               
### JRE的作用
JRE的地位就象一台PC机一样，我们写好的Win32应用程序需要操作系统帮我们运行，同样的，我们编写的Java程序也必须要JRE才能运行。所以当你装完JDK后，如果分别在硬盘上的两个不同地方安装了两套JRE，那么你可以想象你的电脑有两台虚拟的Java PC机，都具有运行Java程序的功能。所以我们可以说，只要你的电脑安装了JRE，就可以正确运行Java应用程序。
          
### JVM简介
JVM是Java Virtual Machine（Java虚拟机）的缩写，JVM是一种用于计算设备的规范，它是一个虚构出来的计算机，是通过在实际的计算机上仿真模拟各种计算机功能来实现的。Java虚拟机包括一套字节码指令集、一组计算器、一个栈、一个垃圾回收堆和一个存储方法域。JVM屏蔽了与具体操作系统平台相关的信息，使Java程序只需生成在Java虚拟机上运行的目标代码（字节码），就可以在多种平台上不加修改地运行。JVM在执行字节码时，实际上最终还是把字节码解释成具体平台上的机器指令执行。      
JVM是JRE的一部分。它是一个虚构出来的计算机，是通过在实际的计算机上仿真模拟各种计算机功能来实现的。JVM有自己完善的硬件架构，如处理器、堆栈、寄存器等，还具有相应的指令系统。Java语言最重要的特点就是跨平台运行。使用JVM就是为了支持与操作系统无关，实现跨平台。
         
### JVM的作用
Java中的所有类，必须装载到JVM中才能运行，这个装载工作是由JVM中的类装载器完成的，类装载器所做的工作实质是把类文件从硬盘读取到内存中。    
JVM对中央处理器（CPU）所执行的一种软件操作，用于执行编译过的Java程序码（Applet与应用程序）。
     
JVM就是我们常说的java虚拟机，它是整个java实现跨平台的最核心的部分，所有的java程序会首先被编译为.class的类文件，这种类文件可以在虚拟机上执行。也就是说class并不直接与机器的操作系统相对应，而是经过虚拟机间接与操作系统交互，由虚拟机将程序解释给本地系统执行。当然只有JVM还不能成class的执行，因为在解释class的时候JVM需要调用解释所需要的类库lib，而jre包含lib类库。
    
JVM屏蔽了与具体操作系统平台相关的信息，使得Java程序只需生成在Java虚拟机上运行的目标代码（字节码），就可以在多种平台上不加修改地运行。
      
### JVM的特性
1. 移植性
无论是GC还是Hotspot都可以用在任何Java可用的地方。比如说，JRuby可以运行在其他平台上，Rails应用就可以运行在IBM主机上的JRuby上，而且这台IBM主机运行的是CP/CMS。实际上，由于Java和OpenJDK项目的开源，我们正在看到越来越多的平台的衍生，因此JVM的移植性也将越来越棒。
       
2. 成熟
JVM已有很多年的历史，许多开发者为他做出了许多贡献，使得它的性能一次又一次得提升，让JVM变得更加稳定、快读和广泛。
      
3. 覆盖面
JRuby和JVM上的其他语言项目已经被开发者所承认，一个典型的例子是invokedynamic specification (aka JSR292)。JSR越来越配合新的语言，JVM已不再是Java一个人定制规则。JVM正在构建成为类如JRuby等项目的优良平台。
        
### JVM的工作原理
JVM是Java的核心和基础，在Java编译器和OS平台之间的虚拟处理器。它是一种利用软件方法实现的抽象的计算机基于下层的操作系统和硬件平台，可以在上面执行Java的字节码程序。
        
![JVM工作原理图](http://www.51gjie.com/Images/image1/gx3ppqm1.f4k.jpg)
          
Java编译器只面向JVM，生成JVM能理解的代码或字节码文件。Java源文件经编译成字节码程序，通过JVM将每一条指令翻译成不同平台机器码，通过特定平台运行。
      
JVM在整个JDK中处于最底层，负责于操作系统的交互，用来屏蔽操作系统环境，提供一个完整的Java运行环境，因此也就是虚拟计算机，操作系统装入JVM是通过JDK中的`Java.exe`来完成，分为四个步骤：   
1. 创建JVM装载环境和配置
2. 装载JVM.dll
3. 初始化JVM.dll并挂界到JNIENV（JNI调用接口）实例
4. 运行Java程序
       
### JVM执行顺序
1. 加载`.class`文件
2. 管理并分配内存
3. 执行垃圾收集
     
JRE（Java运行时环境）由JVM构造的Java程序的运行环，也就是Java程序运行的环境，但是它同时是一个操作系统的一个应用程序一个进程，因此他也有自己的运行的生命周期，也有自己的代码和数据空间。JVM在整个JDK中处于最底层，负责于操作系统的交互，用来屏蔽操作系统环境，提供一个完整的Java运行环境，因此也就是虚拟计算机。
         
### JVM的生命周期
+ JVM实例对应了一个独立运行的Java程序，它是进程级别。
 - 启动。启动一个Java程序时，一个JVM实例就产生了，任何一个用于`public static void main(Sreing[] args)`函数的class都可以作为JVM实例运行的起点。
 - 运行。main()作为该程序初始线程的起点，任何其他线程均由该线程启动。JVM内部有两种线程：守护线程和非守护线程，main()属于非守护线程，守护线程通常由JVM自己使用，Java程序也可以表明自己创建的线程是守护线程。
 - 消亡。当程序中的所有非守护线程都终止时，JVM才退出；若安全管理器允许，程序也可以使用Runtime类或者System.exit()来退出。
+ JVM执行引擎实例则对应了属于用户运行程序的线程，它是线程级别的。
       
### JVM原理结构
![JVM原理结构](http://www.51gjie.com/Images/image1/qxumqim2.o4l.jpg)
         

