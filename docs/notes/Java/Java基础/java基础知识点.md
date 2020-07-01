# 来自网络资源，仅用于学习
>来源[链接](https://snailclimb.top/JavaGuide/#/java/Java%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86)

# Java基础知识
## Java入门            
### 面向对象和面向过程的区别
- 面向过程：面向过程性能比面向对象高。因为类调用时需要示例化，开销比较大，比较消耗资源，所以性能是最重要的考量因素。比如单片机、嵌入式开发、Linux /Unix等一般采用面向过程开发。但是，面向过程没有面向对象易维护、易复用、易扩展。
- 面向对象：面向对象易维护、易复用、易扩展。因为面向对象有封装、继承、多态性的特性，所以可以设计出低耦合的系统，使系统更加灵活、更加易于维护。但是，面向对象性能比面向过程低。
              
>这个并不是根本原因，面向过程也需要分配内存，计算内存偏移量，Java性能差的主要原因并不是因为它是面向对象语言，而是Java是半编译语言，最终的执行代码并不是可以直接被CPU执行的二进制机械码。

>而面向过程语言大多都是直接编译成机械码在电脑上执行，并且其它一些面向过程的脚本语言性能也并不一定比Java好。
           
### Java语言的特点
1. 简单易学
2. 面向对象（封装、继承、多态）
3. 平台无关性（Java虚拟机实现平台无关性）
4. 可靠性
5. 安全性
6. 支持多线程（C++语言没有内置的多线程机制，因此必须调用操作系统的多线程功能来进行多线程程序设计，而Java语言却提供了多线程支持）
7. 支持网络编程并且很方便（Java语言诞生本身就是为了简化网络编程设计的，因此Java语言不仅支持网络编程而且很方便）
8. 编译与解释并存

### JVM
Java虚拟机（JVM）是运行Java字节码的虚拟机。JVM有针对不同系统的特定实现（Windows,Linux,macOS）,目的是使用相同的字节码，它们都会给出相同的结果。

### 字节码以及采用字节码的好处
>在Java中，JVM可以理解的代码就叫做**字节码**（即扩展名为**.class**的文件），它不面向任何特定的处理器，只面向虚拟机。Java语言通过字节码的方式，在一定程度上解决了传统解释型原因呢执行效率低的问题，同时又保留了解释型语言可移植的特点。所以Java程序运行时比较高效，而且，由于字节码并不针对一种特定的机器，因此，由于字节码并不针对一种特定的机器，因此，Java程序无须重新编译便可在多种不同操作系统的计算机运行。
           
Java程序从源代码到运行一般有下面3步：
            
![](../../../pict/3.png)
             
我们需要格外注意的是 .class->机器码 这一步。在这一步 JVM 类加载器首先加载字节码文件，然后通过解释器逐行解释执行，这种方式的执行速度会相对比较慢。而且，有些方法和代码块是经常需要被调用的(也就是所谓的热点代码)，所以后面引进了 JIT 编译器，而JIT 属于运行时编译。当 JIT 编译器完成第一次编译后，其会将字节码对应的机器码保存下来，下次可以直接使用。而我们知道，机器码的运行效率肯定是高于 Java 解释器的。这也解释了我们为什么经常会说 Java 是编译与解释共存的语言。
          
>HotSpot采用了惰性评估(Lazy Evaluation)的做法，根据二八定律，消耗大部分系统资源的只有那一小部分的代码（热点代码），而这也就是JIT所需要编译的部分。JVM会根据代码每次被执行的情况收集信息并相应地做出一些优化，因此执行的次数越多，它的速度就越快。JDK 9引入了一种新的编译模式AOT(Ahead of Time Compilation)，它是直接将字节码编译成机器码，这样就避免了JIT预热等各方面的开销。JDK支持分层编译和AOT协作使用。但是 ，AOT 编译器的编译质量是肯定比不上 JIT 编译器的。
         
总结：        
Java虚拟机（JVM）是运行Java字节码的虚拟机。JVM有针对不同胸痛的特定实现（Windows,Linux,macOS），目的是使用相同的字节码，它们都会给出相同的结果。字节码和不同系统的JVM实现是Java语言“一次编译，随处可以运行”关键所在。
         
### JDK
JDK是Java Development Kit，它是功能齐全的Java SDK。它拥有JRE所拥有的一切，还有编译器（javac）和工具（如javadoc和jdb）。它能够创建和编译程序。
           
### JRE
JRE是Java运行时环境。它是运行已编译Java程序所需的所有内容的集合，包括Java虚拟机（JVM），Java类库，Java命令和其他的一些基础构件。但是，它不能用于创建新程序。
　　　　　　　　　
>如果你只是为了运行一下 Java 程序的话，那么你只需要安装 JRE 就可以了。如果你需要进行一些 Java 编程方面的工作，那么你就需要安装JDK了。但是，这不是绝对的。有时，即使您不打算在计算机上进行任何Java开发，仍然需要安装JDK。例如，如果要使用JSP部署Web应用程序，那么从技术上讲，您只是在应用程序服务器中运行Java程序。那你为什么需要JDK呢？因为应用程序服务器会将 JSP 转换为 Java servlet，并且需要使用 JDK 来编译 servlet。
          
### Oracle JDK和OpenJDK的对比
>问：OpenJDK存储库中的源代码与用于构建Oracle JDK的代码之间有什么区别？
           
>答：非常接近 - 我们的Oracle JDK版本构建过程基于OpenJDK 7构建，只添加了几个部分，例如部署代码，其中包括Oracle的Java插件和Java WebStart的实现，以及一些封闭的源代码派对组件，如图形光栅化器，一些开源的第三方组件，如Rhino，以及一些零碎的东西，如附加文档或第三方字体。展望未来，我们的目的是开源Oracle JDK的所有部分，除了我们考虑商业功能的部分。
              
总结：    
1. Oracle JDK大概每6个月发一次主要版本，而OpenJDK版本大概每三个月发布一次。但这不是固定的，我觉得了解这个没啥用处。详情参见：https://blogs.oracle.com/java-platform-group/update-and-faq-on-the-java-se-release-cadence。
2. OpenJDK 是一个参考模型并且是完全开源的，而Oracle JDK是OpenJDK的一个实现，并不是完全开源的；
3. Oracle JDK 比 OpenJDK 更稳定。OpenJDK和Oracle JDK的代码几乎相同，但Oracle JDK有更多的类和一些错误修复。因此，如果您想开发企业/商业软件，我建议您选择Oracle JDK，因为它经过了彻底的测试和稳定。某些情况下，有些人提到在使用OpenJDK 可能会遇到了许多应用程序崩溃的问题，但是，只需切换到Oracle JDK就可以解决问题；
4. 在响应性和JVM性能方面，Oracle JDK与OpenJDK相比提供了更好的性能；
5. Oracle JDK不会为即将发布的版本提供长期支持，用户每次都必须通过更新到最新版本获得支持来获取最新版本；
6. Oracle JDK根据二进制代码许可协议获得许可，而OpenJDK根据GPL v2许可获得许可。
           
### Java和C++的区别
- 都是面向对象的语言，都支持封装、继承和多态
- Java不提供指针来直接访问内存，程序内存更加安全
- Java的类是单继承，C++支持多重继承；虽然Java的类不可以多继承，但是接口可以多继承
- Java有自动内存管理机制，不需要程序员手动释放无用内存
           
### Java程序的主类以及应用程序和小程序的主类有何不同
一个程序中可以有很多个类，但只能有一个类是主类。在Java应用程序中，这个主类是指包含main()方法的类。而在Java小程序中，这个主类是一个继承自系统类JApplet或Applet的子类。应用程序的主类不一定要求是public类，但小程序的主类要求必须是public类。主类是Java程序执行的入口处。
           
### Java应用程序和小程序的差别
简单说应用程序是从主线程启动（也就是**main()**方法）。applet小程序没有**main()**方法，主要是嵌在浏览器页面上运行（调用**init()**或者**run()**来启动），嵌入浏览器这点跟flash的小游戏类似。

## Java语法      
### 字符型常量和字符串常量的区别
1. 形式上：字符常量是单引号引起的一个字符；字符串常量是双引号引起的若干个字符
2. 含义上：字符常量相当于一个整型值（ASCII 值），可以参加表达式运算；字符串常量代表一个地址值（该字符串在内存中存放位置）
3. 占内存大小：字符常量只占2个字节；字符串常量占若干个字节（至少一个字符结束标志）（**注意：char在Java中占连个字节**）
            
![](../../../pict/86735519.jpg)
        
### 注释
Java中有三种注释：     
1. 单行注释
2. 多行注释
3. 文档注释
       
### 标识符和关键字的区别
标识符：为程序、类、变量、方法等取名字。     
关键字：有其特殊含义的标识符，被用来特定的地方的标识符。
        
### Java中常见的关键字
访问控制：private,protected,public      
类、方法和变量修饰符：abstract,class,extends,final,implements,interface,native,new static,strictfp,synchronized, transient,volatile	      
程序控制：break,continue,return,do,while,if,else,for,instanceof,switch,case,default      
错误处理：try,catch,throw,throws,finally    
包相关：import,package    
基本类型：boolean,byte,char,double,float,int,long,short,null,true,false      
变量引用：super,this,void     
保留字：goto,const
       
### 自增自减运算符
++和--运算符可以放在操作数之前，也可以放在操作数之后，当运算符放在操作数之前时，先自增/减，再赋值；当运算符放在操作数之后时，先赋值，再自增/减。例如，当“b=++a”时，先自增（自己增加 1），再赋值（赋值给 b）；当“b=a++”时，先赋值(赋值给 b)，再自增（自己增加 1）。也就是，++a 输出的是 a+1 的值，a++输出的是 a 值。用一句口诀就是：“符号在前就先加/减，符号在后就后加/减”。

### continue,break和return的区别
在循环结构中，当循环条件不满足或者循环次数达到要求时，循环会正常结束。但是，有时候可能需要在循环的过程中，当发生某种条件之后，提前终止循环，这就需要用到以下几个关键词：
1. continue：指跳出当前的这一次循环，继续下一次循环。
2. break：指跳出整个循环体，继续执行循环下面的语句。

return用于跳出所在方法，结束该方法的运行。return一般有两种用法：
1. return：直接使用return结束方法执行，用于没有返回值函数的方法。
2. return value：return一个特定值，用于返回值函数的方法。
       
### Java泛型，类型擦除，通用的通配符
Java泛型（generics）是jdk5中引入的一个新特性，泛型提供了编译时类型安全检测机制，该机制允许程序员在编译时检测到非法的类型。泛型的本质是参数化类型，也就是说所操作的数据类型被指定为一个参数。
           
Java的泛型是伪泛型，这是因为Java在编译期间，所有的泛型信息都会被擦掉，这也就是通常所说的类型擦除。      
     
常用的通配符：T，E，K，V，？。     
- ？ 表示不确定的Java类型
- T(type)表示具体的一个Java类型
- K V (key value) 分别代表Java键值中key value
- E(element)代表element
      
### ==与equals
==：它的作用是判断两个对象的地址是不是相等。即，判断两个对象是不是同一个对象（基本数据类型==比较的是值，引用数据类型==比较的是内存地址）。
         
equals()：他的作用也是判断两个对象是否相等。但它一般有两种使用情况：
             
- 情况1：类没有覆盖equals()方法。则通过equals()比较该类的两个对象时，等价于通过“==”比较两个对象。
- 情况2：类覆盖了equals()方法。一般，我们都覆盖了equals()方法来比较两个对象的内容是否相等；若它们的内容相等，则返回true（即，认为这两个对象相等）。
     
如：      
       
```java
public class test1 {
    public static void main(String[] args) {
        String a = new String("ab"); // a 为一个引用
        String b = new String("ab"); // b为另一个引用,对象的内容一样
        String aa = "ab"; // 放在常量池中
        String bb = "ab"; // 从常量池中查找
        if (aa == bb) // true
            System.out.println("aa==bb");
        if (a == b) // false，非同一对象
            System.out.println("a==b");
        if (a.equals(b)) // true
            System.out.println("aEQb");
        if (42 == 42.0) { // true
            System.out.println("true");
        }
    }
}
```
              
说明：     
- String中的equals方法是被重写过的，因为object的equals方法是比较的对象的内存地址，而String的equals方法比较的是对象的值。
- 当创建String类型的对象时，虚拟机会在常量池中查找有没有已经存在的值和要创建的值相同的对象，如果有就把它赋给当前引用。如果没有就在常量池中重新创建一个String对象。

### hashCode与equals
**hashCode()**
hashCode()的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。hashCode()定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode()函数。
       
#### 为什么要有hashCode
我们以“HashSet 如何检查重复”为例子来说明为什么要有 hashCode： 当你把对象加入 HashSet 时，HashSet 会先计算对象的 hashcode 值来判断对象加入的位置，同时也会与其他已经加入的对象的 hashcode 值作比较，如果没有相符的hashcode，HashSet会假设对象没有重复出现。但是如果发现有相同 hashcode 值的对象，这时会调用 equals（）方法来检查 hashcode 相等的对象是否真的相同。如果两者相同，HashSet 就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。这样我们就大大减少了 equals 的次数，相应就大大提高了执行速度。
                     
通过我们可以看出：hashCode() 的作用就是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。hashCode()在散列表中才有用，在其它情况下没用。在散列表中hashCode() 的作用是获取对象的散列码，进而确定该对象在散列表中的位置。
            
#### hashCode()与equals()的相关规定
1. 如果两个对象相等，则hashCode一定也是相同的
2. 两个对象相等，对两个对象分别调用equals方法都返回true
3. 两个对象有相同多的hashCode值，它们也不一定是相等的
4. 因此，equals方法被覆盖过，则hashCode方法也必须被覆盖
5. hashCode()的默认行为是对堆上的对象产生独特值。如果没有重写hashCode()，则该class的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）

## 基本数据类型
### Java中的几种基本数据类型，对应的包装类型，以及各自占用的字节。
Java中有**8**种数据类型，分别为：
1. 6种数字类型：byte、short、int、long、float、double
2. 1种字符类型：char
3. 1种布尔类型：boolean
      
这八种基本类型对应的包装类型分别为：byte,short,integer,long,float,double,character,boolean。
        
|基本类型|位数|字节|默认值|
|:-:|:-:|:-:|:-:|
|int|32|4|0|
|short|16|2|0|
|long|64|8|oL|
|byte|8|1|0|
|char|16|2|'u0000'|
|float|32|4|0f|
|double|64|8|0d|
|boolean|1||false|

注意：     
1. Java里使用long类型的数据一定要在数值后面加上L，否则将作为整型解析。
2. `char a='h'` char:单引号，`String a="hello"` String：双引号。
       
### 自动装箱与拆箱
- 装箱：将基本类型用它们对应的引用类型包装起来
- 拆箱：将包装类型转换为基本类型
        
例子：
      
```java
  Integer i1 = 40;
  Integer i2 = 40;
  Integer i3 = 0;
  Integer i4 = new Integer(40);
  Integer i5 = new Integer(40);
  Integer i6 = new Integer(0);

  System.out.println("i1=i2   " + (i1 == i2));
  System.out.println("i1=i2+i3   " + (i1 == i2 + i3));
  System.out.println("i1=i4   " + (i1 == i4));
  System.out.println("i4=i5   " + (i4 == i5));
  System.out.println("i4=i5+i6   " + (i4 == i5 + i6));   
  System.out.println("40=i5+i6   " + (40 == i5 + i6));     

```
       
其结果为：
      
```java
i1=i2   true
i1=i2+i3   true
i1=i4   false
i4=i5   false
i4=i5+i6   true
40=i5+i6   true

```
        
解释：     
语句 i4 == i5 + i6，因为+这个操作符不适用于 Integer 对象，首先 i5 和 i6 进行自动拆箱操作，进行数值相加，即 i4 == 40。然后 Integer 对象无法与数值进行直接比较，所以 i4 自动拆箱转为 int 值 40，最终这条语句转为 40 == 40 进行数值比较。
       
## 方法（函数）
### 方法的返回值，返回值在类的方法里的作用。
方法的返回值是指我们获取到的某个方法体中的代码执行后产生的结果（前提是该方法可能产生结果）。返回值的作用是接收出结果，使得它可以用于其他的操作。
        
### 为什么Java中只有值传递。
专业术语：按值调用（call by value）表示方法接收的是调用者提供的值，而按引用调用（call by reference）表示方法接收的是调用者提供的变量地址。一个方法可以修改传递引用所对应的变量值，而不能修改传递值调用所对应的变量值。
       
Java程序设计语言总是采用按值调用。也就是说，方法的到的是所有参数值的一个拷贝，也就是说，方法不能修改传递给它的任何参数变量的内容。
     
例子：     
```java
public static void main(String[] args) {
    int num1 = 10;
    int num2 = 20;

    swap(num1, num2);

    System.out.println("num1 = " + num1);
    System.out.println("num2 = " + num2);
}

public static void swap(int a, int b) {
    int temp = a;
    a = b;
    b = temp;

    System.out.println("a = " + a);
    System.out.println("b = " + b);
}

```
     
结果：     
```java
a = 20
b = 10
num1 = 10
num2 = 20
```
         
在 swap 方法中，a、b 的值进行交换，并不会影响到 num1、num2。因为，a、b 中的值，只是从 num1、num2 的复制过来的。也就是说，a、b 相当于 num1、num2 的副本，副本的内容无论怎么修改，都不会影响到原件本身。
      
Java中方法参数的使用情况：
- 一个方法不能修改一个基本数据类型的参数（即数值型或布尔型）
- 一个方法可以改变一个对象的状态
- 一个方法不能让对象参数引用一个新的对象
      
### 重载和重写的区别
重载是同样的一个方法能够根据输入数据的不同，做出不同的处理。       
重写是当子类继承父类的相同方法，输入数据一样，但要做出有别于父类的响应时，就要覆盖父类方法。       
重载发生在同一个类中，方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以不同。     
重写发生在运行期，是子类对父类的允许访问的方法的实现过程进行重新编写。重写就是子类对父类方法的重新改造，外部样子不能改变，内部逻辑可以改变。

### 深拷贝和浅拷贝
- 浅拷贝：对基本数据类型进行值传递，对引用数据类型进行引用传递般的拷贝，此为浅拷贝。
- 深拷贝：对基本数据类型进行值传递，对引用数据类型，创建一个新的对象，并复制其内容，此为深拷贝。
      
### 方法的四种类型
1. 无参数返回值的方法
      
```java
// 无参数无返回值的方法(如果方法没有返回值，不能不写，必须写void，表示没有返回值)
public void f1() {
    System.out.println("无参数无返回值的方法");
}
```
      
2. 有参数无返回值的方法
       
```java
/**
* 有参数无返回值的方法
* 参数列表由零组到多组“参数类型+形参名”组合而成，多组参数之间以英文逗号（,）隔开，形参类型和形参名之间以英文空格隔开
*/
public void f2(int a, String b, int c) {
    System.out.println(a + "-->" + b + "-->" + c);
}

```
      
3. 有返回值无参数的方法
      
```java
// 有返回值无参数的方法（返回值可以是任意的类型,在函数里面必须有return关键字返回对应的类型）
public int f3() {
    System.out.println("有返回值无参数的方法");
    return 2;
}

```
       
4. 有返回值有参数的方法
       
```java
// 有返回值有参数的方法
public int f4(int a, int b) {
    return a * b;
}

```
      
5. return 在无返回值方法的特殊使用
       
```java
// return在无返回值方法的特殊使用
public void f5(int a) {
    if (a>10) {
    return;//表示结束所在方法 （f5方法）的执行,下方的输出语句不会执行
}
    System.out.println(a);
}

```