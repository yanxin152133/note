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