# 代码仓库地址
欢迎下载：[GitHub](https://github.com/yanxin152133/java)
      
运行环境：    
- IntelliJ IDEA 2019.1.3(Ultimate Edition)
- jdk 1.8.0_211
       
# Java8手册
文件名为**jdk1.8.CHM**即为Java8手册。
      
打不开参考下面链接：    
- [解决win10中无法打开CHM文件的方法](https://blog.csdn.net/qq_14998713/article/details/52155834)
        
# Java 基础
# Java简介
<!--more-->
Java是一门面向对象编程语言，不仅吸收了C++语言的各种优点，还摒弃了C++里难以理解的多继承、指针等概念，因此Java语言具有功能强大和简单易用两个特征。Java语言作为静态面向对象编程语言的代表，极好地实现了面向对象理论，允许程序员以优雅的思维方式进行复杂的编程。      

Java具有简单性、面向对象、分布式、健壮性、安全性、平台独立与可移植性、多线程、动态性等特点 。Java可以编写桌面应用程序、Web应用程序、分布式系统和嵌入式系统应用程序等。
     
[详情](https://baike.baidu.com/item/Java/85979?fr=aladdin)
     
# 运行环境搭建
## 下载
JDK建议使用1.8及以上的版本。     
官方下载路径：[jdk下载路地址](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
      
## 安装
双击下载软件，一路单击下一步即可。     
    
## 配置环境变量
**Windows**：右击【我的电脑】→【属性】→【高级系统设置】→【环境变量】→【系统变量】→【新建】，接着如下图所示：    
![java_home](https://farm8.staticflickr.com/7873/40480682053_903c92b01b_b.jpg)
     
在【系统变量】的path中添加 **%JAVA_HOME%\bin**。
     
验证，如下图所示：    
![java](https://farm8.staticflickr.com/7860/40480681993_9a639b1dc2_b.jpg)

# Hello World
```java
public class helloworld {
    public static void main(String[] args) {
        System.out.println("helloworld");
    }
}
```
          
# 工具
## Intellij IDEA
下载路径：[indea U](https://www.jetbrains.com/idea/download/download-thanks.html?platform=windows)
      
### 激活（针对学生的免费使用计划）
参考：[Intellij IDEA的下载和使用（针对学生的免费使用计划）](https://blog.csdn.net/iemdm1110/article/details/53365881)
       
# 注释、标识符命名规则及Java中的关键字
## 1. Java注释
```
1. 单行注释：//
2. 多行注释：/*。。。。。*/
3. 文档注释：/**。。。*/
```
    
## 2. 标识符命名
```
标识符定义：Java语言中，对于变量、常量、函数、语句块也有名字，我们统统称为Java标识符。

标识符作用：标识符是用来给类、对象、方法、常量、接口和自定义数据类型命令的。
     
标识符命名规则：Java标识符由数字、字母和下划线（_），美元符号（$）组成。在Java中是区分大小写的，而且还要求首位不能是数字。最重要的是，Java关键字不能当作Java标识符。
```
     
## 3. Java关键字
参考：[Java 关键字总结](http://cyw3.github.io/YalesonChan/2016/Java-key.html)	 	 	 	 
       
# Java基本数据类型
## 1. 数据类型分类
![](https://live.staticflickr.com/65535/48287266636_32ed239f62_z.jpg)
      
## 2. 整数类型
     
|序号|数据类型|大小/位|可表示的数据范围|
|--|--|--|--|
|1|byte(位)|8|-2<sup>7</sup>到（2<sup>6</sup>-1）|
|2|short(整型)|16|-2<sup>15</sup>到（2<sup>15</sup>-1）|
|3|int(整型)|32|-2<sup>31</sup>到（2<sup>31</sup>-1）|
|4|long(长整型)|64|-2<sup>63</sup>到（2<sup>63</sup>-1）|
      
Byte数据范围表示   
     
|符号位|1|1|1|1|1|1|1|1|
|--|--|--|--|--|--|--|--|--|
|||||||||||

符号位0表示正   范围  00000000~01111111     
符号位1表示负   范围  10000000~11111111（减一取反）
      
代码实例：    
```java
package com.java.chap03;

/**
 * @author Yan
 * @date 2019/7/16 13:52
 */
public class Demo1 {
    public static void main(String[] args) {
        //定义一个int类型的变量
        int a;
        //给变量a赋值
        a=1;
        System.out.println(a);

        //定义一个int类型的变量a2
        int a2=1;
        System.out.println("a2="+a2);

        //定义一个byte类型的变量b
        byte b=3;
        System.out.println("b="+b);

        //定义一个short类型的变量
        short s=4;
        System.out.println("s="+s);


        //定义一个long类型的变量l
        long l=5;
        System.out.println("l="+l);

        int a11=1;
        int a22=2;
        int a3=a11+a22;
        System.out.println("a1+a2="+a3);
    }
}
```
      
## 3. 浮点类型

|序号|数据类型|大小/位|可表示的数据范围|
|---|---|---|---|
|1|float(单精度)|32|-3.4E38(-3.4x10<sup>38</sup>) 到 3.4E38(3.4x10<sup>38</sup>))|
|2|double(双精度)|64|-1.7E308(-1.7x10<sup>308</sup>) 到 1.7E308(1.7x10<sup>308</sup>))|
      
代码示例：       
```java
package com.java.chap03;

/**
 * @author Yan
 * @date 2019/7/16 13:53
 */
public class Demo2 {
    public static void main(String[] args) {
        //定义一个float类型的变量f
        //小数默认是double类型，所以必须加一个f,来表示float类型
        float f=1.1f;
        System.out.println("f="+f);

        //定义一个double类型变量d
        double d=1.2;
        System.out.println("d="+d);

        //获取float的最大值
        float maxF=Float.MAX_VALUE;
        System.out.println("float最大值："+maxF);
        //获取float的最小值
        float minF=Float.MIN_VALUE;
        System.out.println("float最小值："+minF);
    }
}

```
      
## 4. 字符型
字符型常量有3种表示形式。char     
    1. 直接通过单个字符来指定字符型常量，如‘A’，‘b’，‘5’；
    2. 通过转义字符表示特殊字符型常量，如‘\n’,‘\\’;
    3. 直接使用Unicode值来表示字符型常量，如‘\u66f9’，‘\yu950b’；
        
|转义字符|说明|
|-------|----|
|\b|退格|
|\n|换行|
|\t|制表符|
|\"|双引号|
|\'|单引号|
|\\|反斜杠|
|\r|回车符|
      
代码示例:        
```java
package com.java.chap03;

/**
 * @author Yan
 * @date 2019/7/16 13:53
 */
public class Demo3 {
    public static void main(String[] args) {
        //定义一个单个字符
        char c1='A';
        System.out.println("c1="+c1);


        //定义一个反斜杠字符
        char c2='\\';
        System.out.println("c2="+c2);


        //用Unicode编码输出自己的名字
        char c3='\u66f9';
        char c4='\u950b';
        System.out.println("c3="+c3);
        System.out.println("c4="+c4);
    }
}
```
      
## 5. 布尔类型
布尔类型的变量只有true(真)和false(假)两种。  

```java
package com.java.chap03;

/**
 * @author Yan
 * @date 2019/7/16 13:53
 */
public class Demo4 {
    public static void main(String[] args) {
        //定义一个布尔类型变量b1
        boolean b1=true;
        System.out.println("b1="+b1);
        //定义一个布尔类型变量b2
        boolean b2=false;
        System.out.println("b2="+b2);
    }
}

```
      
## 6. 基本类型的类型转换
    1. 自动类型转换
    条件： 
         1. 转换前后的数据类型兼容；
         2. 转换后的数据类型的表示范围要比转换前的大；
        
    2. 强制类型转换
      
代码示例：    
            
```java
package com.java.chap03;

/**
 * @author Yan
 * @date 2019/7/16 13:53
 */
public class Demo5 {
    public static void main(String[] args) {
        //自动类型转换
        short s=1;
        int i;
        //自动类型转换 short类型转成int类型
        i=s;
        System.out.println("i="+i);


        //强制类型转换
        double d=1.333;
        float f;
        //把double类型的数据强制转换成float类型
        f=(float) d;
        System.out.println("f="+f);
    }
}

```
      
# Java运算符与表达式
![](https://live.staticflickr.com/65535/48287869506_1ed621abc2_z.jpg)
       
##  1. 赋值运算符
符号：=（赋值）
```java
package com.java.chap04;

/**
 * @author Yan
 * @date 2019/7/16 13:01
 */
public class Demo1 {
    public static void main(String[] args) {
        //定义变量a
        int a;
        //给变量a赋值
        a=1;
        System.out.println("a="+a);

        //定义变量a，并且给a赋值
        int a2=2;
        System.out.println("a2="+a2);
    }
}
```
     
## 2. 算数运算符
符号：+（加），-（减），*（乘），/（除），%（取模）
```java
package com.java.chap04;

/**
 * @author Yan
 * @date 2019/7/16 13:07
 */
public class Demo2 {
    public static void main(String[] args) {
        int a=10;
        int b=3;

        //+运算符
        System.out.println(a+"+"+b+"="+(a+b));

        //-运算符
        System.out.println(a+"-"+b+"="+(a-b));

        //*运算符
        System.out.println(a+"*"+b+"="+(a*b));

        // /运算符
        System.out.println(a+"/"+b+"="+(a/b));

        //%运算符
        System.out.println(a+"%"+b+"="+(a%b));
    }
}
```
      
## 3. 自增与自减运算符
符号：++（自增），--（自减）       
**重点：a++和++a的区别**
```java
package com.java.chap04;

/**
 * @author Yan
 * @date 2019/7/16 13:13
 */
public class Demo3 {
    public static void main(String[] args) {
        int a = 1;
        //a++表示先做赋值操作，然后自增
        /*
        int b=a++;
        System.out.println("b="+b);
        System.out.println("a="+a);
         */

        //++a表示先自增，然后赋值操作
        int b=++a;
        System.out.println("b="+b);
        System.out.println("a="+a);
    }
}

```
       
## 4. 逻辑运算符
符号：&&（与），&（不短路与），||（或），|（不短路或），!(非)，^（亦或）
```java
package com.java.chap04;

/**
 * @author Yan
 * @date 2019/7/16 13:53
 */
public class Demo4 {
    public static void main(String[] args) {
        // && 与  前后两个操作数必须都是true才返回true，否则返回false
        boolean b1 = (5 < 3) && (4 > 5);
        System.out.println("b1 = " + b1);

        //& 不短路与
        boolean b2 = (5 < 3) & (4 > 5);
        System.out.println("b2 = " + b2);

        //一般都使用 &&
        //原因：效率高

        // || 或 只要两个操作数中有一个是true，就返回true，否则返回false
        boolean b3 = (2 < 3) || (4 > 5);
        System.out.println("b3 = " + b3);

        // | 不短路或
        boolean b4 = (2 < 3) | (4 > 5);
        System.out.println("b4 = " + b4);

        // ! 非，如果操作数为true，返回false，否则返回true
        boolean b5 = !(3 < 4);
        System.out.println("b5 = " + b5);

        // ^ 异或 当两个操作数不相同时，返回true，否则返回false
        boolean b6 = (5 > 4) ^ (4 > 5);
        System.out.println("b6 = " + b6);
    }
}
```
       
## 5. 关系运算符
符号：>(大于)，<(小于)，>=（大于等于），<=(小于等于)，==（等于），!=(不等于)
```java
package com.java.chap04;

/**
 * @author Yan
 * @date 2019/7/16 14:22
 */
public class Demo5 {
    public static void main(String[] args) {
        int a = 2;
        int b = 3;


        // > 大于
        System.out.println(a + ">" + b + ":" + (a > b));

        // < 小于
        System.out.println(a + "<" + b + ":" + (a < b));

        // >= 大于等于
        System.out.println(a + ">=" + b + ":" + (a >= b));

        // <= 小于等于
        System.out.println(a + "<=" + b + ":" + (a <= b));

        // == 等于
        System.out.println(a + "==" + b + ":" + (a == b));

        // != 不等于
        System.out.println(a + "!=" + b + ":" + (a != b));
    }
}
```
     
## 6. 三目运算符
格式：（表达式）？表达式为true返回值A：表达式为false返回值B
```java
package com.java.chap04;

/**
 * @author Yan
 * @date 2019/7/16 14:26
 */
public class Demo6 {
    public static void main(String[] args) {
        //三目运算符
        String s=2>3?"表达式为真":"表达式为假";
        System.out.println("s = " + s);
    }
}

```
       
# Java选择与循环语句
## 1. 程序的选择结构
    1. if 语句
    2. if...else 语句
    3. if...else if...else 语句

```java
package com.java.chap05;

/**
 * @author Yan
 * @date 2019/7/16 15:16
 */
public class Demo1 {
    public static void main(String[] args) {
        int a=-1;
        // if语句
        if (a>0){
            System.out.println(a+"是正数");
        }

        //if...else语句
        if (a>0){
            System.out.println(a+"是正数");
        }else {
            System.out.println(a+"不是正数");
        }

        //if...else if...else
        if (a>0){
            System.out.println(a+"是正数");
        }else if (a<0){
            System.out.println(a+"是负数");
        }else{
            System.out.println(a+"是0");
        }
    }
}
```
   
    4. switch 语句
```java
package com.java.chap05;

import java.util.Scanner;

/**
 * @author Yan
 * @date 2019/7/16 15:22
 */
public class Demo2 {
    public static void main(String[] args) {
        System.out.println("请输入一个数字");
        //定义一个系统输入对象
        Scanner scanner=new Scanner(System.in);
        int n=scanner.nextInt();
        //System.out.println(n);
        switch (n){
            case 1:{
                System.out.println("用户输入的是1");
                break;
            }
            case 2:{
                System.out.println("用户输入的是2");
                break;
            }
            default:{
                System.out.println("用户输入的是其他数字");
            }
        }
    }
}
```
       
## 2. 程序的循环结构
    1. while 循环
    2. do...while 循环
    3. for 循环
    4. for 循环的嵌套
```java
package com.java.chap05;

/**
 * @author Yan
 * @date 2019/7/16 15:31
 */
public class Demo3 {
    public static void main(String[] args) {
        //在控制台输出1到10
        //while 循环语句
        int i = 1;
        while (i < 11) {
            System.out.print(i + "  ");
            i++;
        }

        System.out.println("\n-------------------");


        // do...while 循环语句
        int j = 1;
        do {
            System.out.print(j + "    ");
            j++;
        } while (j < 11);

        System.out.println("\n-------------------");


        //while和do...while的区别
        //while是先判断后执行，do...while是先执行后判断


        // for 循环
        for (int k = 1; k < 11; k++) {
            System.out.printf(k + "   ");
        }

        System.out.println("\n-------------------");


        // for循环的嵌套
        for (int m = 0; m < 10; m++) {
            for (int n = 0; n < 10; n++) {
                System.out.print("m=" + m + "n=" + n+"   ");
            }
            System.out.println();
        }
    }
}
```
    5. 求水仙花数
```java
package com.java.chap05;

/**
 * @author Yan
 * @date 2019/7/16 15:42
 */
public class Demo4 {
    public static void main(String[] args) {
        for (int i=100;i<=999;i++){
            //求出百位数
            int b=i/100;
            //求出十位数
            int s=(i-b*100)/10;
            //求出个位数
            int g=(i-b*100-s*10);

            if (i==g*g*g+s*s*s+b*b*b){
                System.out.println(i+" ");
            }
        }
    }
}
```
      
## 3. 循环结构的控制
    1. break 语句
    结束循环
```java
package com.java.chap05;

/**
 * @author Yan
 * @date 2019/7/16 15:52
 */
public class Demo5 {
    public static void main(String[] args) {
        for (int i=0;i<10;i++){
            for (int j=0;j<10;j++){
                if (i==1){
                    break;
                }
                System.out.print("i="+i+"   j="+j+"  ");

            }
            System.out.println();
        }
    }
}
```
```java
package com.java.chap05;

/**
 * @author Yan
 * @date 2019/7/16 15:55
 */
public class Demo6 {
    public static void main(String[] args) {
        outer:
        for (int i=0;i<10;i++){
            for (int j=0;j<10;j++){
                if (i==1){
                    break outer;
                }
                System.out.print("i="+i+"   j="+j+"  ");

            }
            System.out.println();
        }
    }
}
```
    2. continue 语句
    结束本次循环
```java
package com.java.chap05;

/**
 * @author Yan
 * @date 2019/7/16 15:57
 */
public class Demo7 {
    public static void main(String[] args) {
        for (int i=0;i<10;i++){
            if (i==4){
                continue;
            }
            System.out.print("i="+i+"  ");
        }
    }
}
```
    3. return 语句
    结束方法
```java
package com.java.chap05;

/**
 * @author Yan
 * @date 2019/7/16 15:59
 */
public class Demo8 {
    public static void main(String[] args) {
        for (int i=0;i<10;i++){
            for (int j=0;j<10;j++){
                if (i==1){
                    return;
                }
                System.out.print("i="+i+"   j="+j+"  ");

            }
            System.out.println();
        }
        System.out.println("执行到这里了");
    }
}
```
      
# Java数组
## 1. 数组简介
数组是Java中最常见的一种数据结构，可用于存储多个数据。
     
## 2. 数组的定义
```java
type[] arrayName;或者type arrayName[];   
```
           
实例：     
```java
int []arr; int arr[];    
```
      
```java
package com.java.chap06;

/**
 * @author Yan
 * @date 2019/7/17 14:08
 */
public class Demo1 {
    public static void main(String[] args) {
        //定义一个数组
        int []arr;
        //定义一个数组
        int arr2[];

    }
}

```
## 3. 数组的初始化
    1. 静态初始化
格式     
```java
arrayName=new type[]{element1,element2,element3.....}     
```
          
实例：    
```java
int arr1[]=new int[]{1,2,3}; 
```
          
```java
package com.java.chap06;

/**
 * @author Yan
 * @date 2019/7/17 14:14
 */
public class Demo2 {
    public static void main(String[] args) {
        //定义一个数组，并且静态初始化
        int arr[]=new  int[]{1,2,3};

        //普通的遍历数组方式
        for (int i=0;i<arr.length;i++){
            System.out.println(arr[i]);
        }
        System.out.println("------------");

        
        //foreach方法遍历数组
        for (int j:arr){
            System.out.println(j);
        }
    }
}
```
    
    2. 动态初始化
格式      
```java 
arrayName=new type[length];
```
         
实例：      
```java
int arr2[]=new int[3];
```
           
```java
package com.java.chap06;

/**
 * @author Yan
 * @date 2019/7/17 14:18
 */
public class Demo3 {
    public static void main(String[] args) {
        //定义一个数组，然后动态初始化，长度是3
        int arr[]=new int[3];

        for(int i:arr){
            System.out.println(i);
        }

    }
}

```
     
内存分析     
![](https://live.staticflickr.com/65535/48305077142_c9fb3c2e4b_z.jpg)
      
## 4. 二维数组及多维数组
二维数组静态化初始化 格式：   
```java   
arrayName=new type[]{{element1,element2},{element1,element2},{element1,element2}};    
```
     
实例：     
```java
int[][]arr=new int[][]{1,2,3},{4,5,6},{7,8,9}};
```


二维数组动态初始化 格式：    
```java  
arrayName=new type[length][length];    
```
         
实例：    
```java
int [][]arr2=new int[3][3];
```
      
```java
package com.java.chap06;

/**
 * @author Yan
 * @date 2019/7/17 14:35
 */
public class Demo4 {
    public static void main(String[] args) {
        //定义一个二维数组,并静态初始化
        int [][]arr=new int[][]{{1,2,3},{4,5,6},{7,8,9}};

        //输出
        for (int i=0;i<arr.length;i++){
            for (int j=0;j<arr[0].length;j++){
                System.out.print(arr[i][j]+"  ");
            }
            System.out.println();

        }
        

        //二维数组的动态初始化
        int [][]arr2=new int[3][3];
        for (int i=0;i<arr2.length;i++){
            for (int j=0;j<arr2[0].length;j++){
                System.out.print(arr2[i][j]+"  ");
            }
            System.out.println();

        }

    }
}
```
        
![](https://live.staticflickr.com/65535/48305176832_bedf7286a8_z.jpg)
      
## 5. 起泡法
对4，21，0，-12，-3排序。     
原理：起泡法是从一端开始比较的，第一次循环就是把最大数放到最后一个位置，第二次循环就是把第二最大数放到倒数第二个位置。       
       
||4|21|0|-12|-3|
|-|-|-|-|-|-|
|第1次|4|0|-12|-3|21|
|第2次|0|-12|-3|4|21|
|第3次|-12|-3|0|4|21|
|第4次|-12|-3|0|4|21|
      
```java
package com.java.chap06;

/**
 * @author Yan
 * @date 2019/7/17 14:46
 */
public class Demo5 {
    public static void main(String[] args) {
        int temp;
        int []arr={4,21,0,-12,-3};

        //循环的次数n-1次
        for (int i=0;i<arr.length-1;i++){
            //比较次数n-1-i
            for (int j=0;j<arr.length-1-i;j++){
                //假如前面一个数大于后面一个数，则交换数据
                if (arr[j]>arr[j+1]){
                    temp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;
                }
            }
        }
        for (int i:arr){
            System.out.print(i+"  ");
        }
    }
}
```
       
# Java面向对象
## 1. 面向对象的基本概念
定义：以基于对象的思维去分析和解决问题，万物皆对象；     
三大特性：封装，继承，多态；
       
## 2. 类与对象
### 1. 类与对象的关系
### 2. 类的定义
### 3. 类的创建及使用
```java
package com.java.chap07.sec01;

/**
 * @author Yan
 * @date 2019/7/18 13:39
 * Person类
 */
public class Person {
    String name;    //在类中，定义一个姓名name字符串属性
    int age;         //在类中，定义一个年龄age属性


    public void speak(){
        System.out.println("我叫"+name+"我今年"+age+"岁了");
    }

    public static void main(String[] args) {
        //定义一个Person类的对象zhangsan
        Person zhangsan;
        //实例化对象
        zhangsan=new Person();
        //给对象的name属性赋值
        zhangsan.name="张三";
        zhangsan.age=23;
        zhangsan.speak();
    }
}


```
      
内存分析    

![](https://live.staticflickr.com/65535/48312793817_34c3556633_z.jpg)
       
## 3. 方法
### 1. 方法的定义及简单使用
```java
package com.java.chap07.sec02;

/**
 * @author Yan
 * @date 2019/7/18 13:54
 */
public class People {
    /**
     * 最简单的一个方法定义
     */
    void speak(){
        System.out.println("我叫张三");
    }

    public static void main(String[] args) {
        People zhangsan=new People();
        zhangsan.speak();
    }
}

```
```java
package com.java.chap07.sec02;

/**
 * @author Yan
 * @date 2019/7/18 13:57
 */
public class People2 {

    //形参，入参
    void speak(String name){
        System.out.println("我叫"+name);
    }

    public static void main(String[] args) {
        People2 zhangsan=new People2();
        zhangsan.speak("张三");
    }
}

```
```java
package com.java.chap07.sec02;

/**
 * @author Yan
 * @date 2019/7/18 13:57
 */
public class People3 {

    //形参，入参
    void speak(String name, int age) {
        System.out.println("我叫" + name+"我今年"+age+"岁了");
    }

    public static void main(String[] args) {
        People3 zhangsan = new People3();
        zhangsan.speak("张三", 23);
    }
}

```
```java
package com.java.chap07.sec02;

/**
 * @author Yan
 * @date 2019/7/18 13:57
 */
public class People4 {

    //形参，入参,不固定参数
    void speak(String name, int age,String ...hobbies) {
        System.out.println("我叫" + name + "我今年" + age + "岁了");
        System.out.println("我的爱好：  ");
        for (String hobby:hobbies){
            System.out.print(hobby+"  ");
        }
    }

    public static void main(String[] args) {
        People4 zhangsan = new People4();
        zhangsan.speak("张三", 23,"游泳","唱歌");
    }
}

```
```java
package com.java.chap07.sec02;

/**
 * @author Yan
 * @date 2019/7/18 13:57
 */
public class People5 {

    //返回类型
    int speak(String name, int age,String ...hobbies) {
        System.out.println("我叫" + name + "我今年" + age + "岁了");
        System.out.println("我的爱好：  ");
        for (String hobby:hobbies){
            System.out.print(hobby+"  ");
        }

        //获取爱好的长度
        int totalHobbies=hobbies.length;
        return totalHobbies;
    }

    public static void main(String[] args) {
        People5 zhangsan = new People5();
        int n=zhangsan.speak("张三", 23,"游泳","唱歌");
        System.out.println("\n有"+n+"个爱好");
    }
}

```
### 2. 方法的值传递和引用传递(重点)
```java
package com.java.chap07.sec02;

/**
 * 三围类
 * @author Yan
 * @date 2019/7/18 14:08
 */
class Sanwei{
    int b;   //胸围
    int w;   //腰围
    int h;   //臀围
}


public class People6 {


    /**
     * 报三围
     * @param age 年龄
     * @param sanwei  三围
     */
    void speak(int age,Sanwei sanwei){
        System.out.println("我今年"+age+"岁了,我的三围是"+sanwei.b+","+sanwei.w+","+sanwei.h);
        age=24;
        sanwei.b=80;
    }

    public static void main(String[] args) {
        People6 xiaoli=new People6();
        int age=23;
        Sanwei sanwei=new Sanwei();
        sanwei.b=90;
        sanwei.w=60;
        sanwei.h=90;
        //age传递的是值，sanwei传递的是引用（地址）,c里叫指针
        xiaoli.speak(age,sanwei);
        System.out.println(age);
        System.out.println(sanwei.b);
    }
}

```
### 3. 方法的重载
方法重载定义：方法名称相同，但是参数的类型或者参数的个数不同。
       
```java
package com.java.chap07.sec03;

/**
 * @author Yan
 * @date 2019/7/18 14:22
 */
public class Demo {
    int add(int a,int b){
        System.out.print("方法一:");
        return a+b;
    }

    /**
     * 方法的重载，参数个数不一样
     * @param a
     * @param b
     * @param c
     * @return
     */
    int add(int a,int b,int c){
        System.out.print("方法二：");
        return a+b+c;
    }


    /**
     * 方法的重载，参数的类型不一样
     * @param a
     * @param b
     * @return
     */
    int add(int a,String b){
        System.out.print("方法三：");
        return a+Integer.parseInt(b);
    }
    

    public static void main(String[] args) {
        Demo demo=new Demo();
        System.out.println(demo.add(1,2));
        System.out.println(demo.add(1,2,3));
        System.out.println(demo.add(1,"3"));
    }
}

```
### 4. static静态方法与普通方法
static方法：方法属于类本身；调用方式：1. 类名.方法;2. 对象.方法      
       
普通方法：方法属于类的对象；调用方式：1. 对象.方法
       
```java
package com.java.chap07.sec03;

/**
 * @author Yan
 * @date 2019/7/18 15:33
 */
public class Demo2 {

    void fun1(){
        System.out.println("这是一个普通方法");
    }

    static void fun2(){
        System.out.println("这是一个静态方法");
    }

    public static void main(String[] args) {
        Demo2 demo2=new Demo2();
        //调用普通方法，对象.方法
        demo2.fun1();
        //调用静态方法，类名.方法名
        Demo2.fun2();
        //调用静态方法，对象.方法
        demo2.fun2();
    }
}
```
### 5. 递归方法
求阶乘 1 * 2 * 3... * (n-1) * n    
原理：     

```java
N=5 F(n-1) * 5        
N=4 F(n-1) * 4     
N=3 F(n-1) * 3      
N=2 F(n-1) * 2      
N=1 1   
```
       
```java
package com.java.chap07.sec03;

/**
 * @author Yan
 * @date 2019/7/18 15:38
 */
public class Demo3 {


    /**
     * 非递归
     * @param n
     * @return
     */
    static long notDiGui(int n){
        long result=1;
        for (int i=1;i<=n;i++){
            result=result*i;
        }
        return result;
    }

    /**
     * 递归
     * @param n
     * @return
     */
    static long DiGUi(int n){
        if (n==1){
            return 1;
        }
        return DiGUi(n-1)*n;
    }



    public static void main(String[] args) {
        System.out.println("非递归："+Demo3.notDiGui(5));
        System.out.println("递归:"+Demo3.DiGUi(5));
    }
}
```
       
## 4. 构造方法，this关键字
### 1. 构造方法
构造器是一个特殊的方法，这个特殊方法用于创建实例时可执行初始化；    
假如没有构造方法，系统会自动生成一个默认的无参构造方法；假如有构造方法，系统不会自动生成构造方法；
      
```java
package com.java.chap07.sec04;

/**
 * @author Yan
 * @date 2019/7/18 15:56
 */
public class People {

    // String 类属性默认值是null
    private String name;
    //int 类属性默认值是0
    private int age;


    /**
     * 默认构造方法
     */
    People(){
        System.out.println("默认构造方法");
    }

    /**
     * 有参数的构造方法   构造方法的重载
     */
    People(String name2,int age2){
        name=name2;
        age=age2;
        System.out.println("有参数的构造方法");
    }

    public void say(){
        System.out.println("我叫："+name+"，我今年："+age+"岁了");
    }

    public static void main(String[] args) {
        //People people=new People();
        People people2=new People("张三",23);
        people2.say();
    }
}

```
### 2. this关键字
this表示当前对象     

1. 使用this调用本类中的属性；    
2. 使用this调用构造方法；    

```java
package com.java.chap07.sec04;

/**
 * @author Yan
 * @date 2019/7/18 15:56
 */
public class People2 {

    // String 类属性默认值是null
    private String name;
    //int 类属性默认值是0
    private int age;


    /**
     * 默认构造方法
     */
    People2(){
        System.out.println("默认构造方法");
    }

    /**
     * 有参数的构造方法   构造方法的重载
     */
    People2(String name2, int age2){
        this();
        this.name=name2;
        this.age=age2;
        System.out.println("有参数的构造方法");
    }

    public void say(){
        System.out.println("我叫："+name+"，我今年："+age+"岁了");
    }

    public static void main(String[] args) {
        //People people=new People();
        People2 people2=new People2("张三",23);
        people2.say();
    }
}
```
       
## 5. 访问控制权限及package import关键字
### 1. 访问控制权限
private(私有)   get,set方法     
package（包访问权限）     
protected(子类访问权限)     
public（公共访问权限）      
      
||private|package|protected|public|
|-|-|-|-|-|
|同一个类中|√|√|√|√|
|同一个包中||√|√|√|
|子类中|||√|√|
|全局范围||||√|
       
**Demo1.java**    
```java
package com.java.chap07.sec05;

/**
 * @author Yan
 * @date 2019/7/18 16:16
 */
public class Demo1 {
    /**
     * 定义一个私有的属性a
     */
    private int a;


    public int getA() {
        return a;
    }

    public void setA(int a) {
        this.a = a;
    }
}

```
      
**TestDemo1.java**     
```java
package com.java.chap07.sec05;

/**
 * @author Yan
 * @date 2019/7/18 16:17
 */
public class TestDemo1 {
    public static void main(String[] args) {
        Demo1 demo1=new Demo1();
        demo1.setA(2);
        int a=demo1.getA();
        System.out.println(a);
    }
}

```
### 2. package import 关键字
package 包定义      
import 导入相关类
       
```java
package com.java.chap07.sec05;


import com.java.chap07.sec02.People;

/**
 * @author Yan
 * @date 2019/7/18 16:19
 */
public class Demo2 {
    public static void main(String[] args) {

        //不同包，则需要导入相关类
        People people=new People();
        //在同一个包中，则不需要导入相关类
        Demo1 demo1=new Demo1();
    }
}

```
           
## 6. 内部类
内部类定义：在类的内部定义类；     
内部类优点：可以方便的使用外部类的属性；     
内部类缺点：破环类的基本结构；              
      
**Demo1.java**     
```java
package com.java.chap07.sec06;

/**
 * @author Yan
 * @date 2019/7/18 16:38
 */
public class Outer {
    private int a=1;

    /**
     * 定义内部类
     */
    class Inner{
        public void show(){
            System.out.println(a);
        }
    }


    public void show(){
        Inner inner=new Inner();
        inner.show();
    }

    public static void main(String[] args) {
        Outer outer=new Outer();
        outer.show();
    }
}
```
       
**Demo2.java**      
```java
package com.java.chap07.sec06;

/**
 * @author Yan
 * @date 2019/7/18 16:38
 */
public class Outer2 {
    private int a = 1;

    /**
     * 定义内部类
     */
    class Inner {
        public void show() {
            System.out.println(a);
        }
    }


    public static void main(String[] args) {
        Outer2 outer2 = new Outer2();   //实例化外部类对象
        Outer2.Inner inner = outer2.new Inner();    //实例化内部类对象
        inner.show();
    }
}

```
        
## 7. 代码块
1. 普通代码块
       
```java
package com.java.chap07.sec07;

/**
 * @author Yan
 * @date 2019/7/18 16:49
 */
public class Demo1 {
    public static void main(String[] args) {
        int a=1;
        /**
         * 普通代码块
         */
        {
            a=2;
            System.out.println("普通代码块");
        }
        System.out.println("a="+a);
    }
}

```
2. 构造块
        
```java
package com.java.chap07.sec07;

/**
 * @author Yan
 * @date 2019/7/18 16:52
 */
public class Demo2 {
    /**
     * 构造块
     * @param args
     */
    {
        System.out.println("通用构造块");
    }

    /**
     * 构造方法一
     */
    public Demo2(){
        System.out.println("构造方法一");
    }
    /**
     * 构造方法二
     */
    public Demo2(int i){
        System.out.println("构造方法二");
    }
    /**
     * 构造方法三
     */
    public Demo2(int i,int j){
        System.out.println("构造方法三");
    }


    public static void main(String[] args) {
        new Demo2();    //实例化一个对象  匿名类
        new Demo2(1);
        new Demo2(1,2);
    }
}

```
3. 静态代码块
        
```java
package com.java.chap07.sec07;

/**
 * @author Yan
 * @date 2019/7/18 16:55
 */
public class Demo3 {
    /**
     * 构造块
     */
    {
        System.out.println("通用构造块");
    }

    /**
     * 静态代码块
     */
    static {
        System.out.println("静态代码块");
    }

    /**
     * 构造方法一
     */
    public Demo3(){
        System.out.println("构造方法一");
    }
    /**
     * 构造方法二
     */
    public Demo3(int i){
        System.out.println("构造方法二");
    }
    /**
     * 构造方法三
     */
    public Demo3(int i,int j){
        System.out.println("构造方法三");
    }

    public static void main(String[] args) {
        new Demo3();
        new Demo3(1);
        new Demo3(1,2);

    }
}
```
      
## 8. String 类
### 1. 实例化String对象
方法一：   
```java
String name1="张三";
```
     
方法二：     
```java
String name2=new String("李四");
```
     
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 21:32
 */
public class Demo1 {
    public static void main(String[] args) {
        //实例化String的方式一
        String name1="张三";
        System.out.println("name1:"+name1);

        //实例化String的方式二
        String name2=new String("李四");
        System.out.println("name2:"+name2);
    }
}
```
      
### 2. "==" VS "equals方法"
1. “==”，比较的是引用，“equals方法”比较的是具体内容
       
![](https://live.staticflickr.com/65535/48314990292_7cf024cfee_z.jpg)
      
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 21:39
 */
public class Demo2 {
    public static void main(String[] args) {
        String name1="张三";    //直接赋值方式
        String name2=new String("张三");   //new 的方式
        String name3=name2;     // 传递引用

        //==比较的是引用
        System.out.println("name1==name2:"+(name1==name2));
        System.out.println("name1==name3:"+(name1==name3));
        System.out.println("name2==name3:"+(name2==name3));

        System.out.println("-------------");


        //equals比较的是内容
        System.out.println("name1.equals(name2):"+(name1.equals(name2)));
        System.out.println("name1.equals(name3):"+(name1.equals(name3)));
        System.out.println("name2.equals(name3):"+(name2.equals(name3)));
    }
}
```
### 3. String 两种实例化方式的区别
1. 直接赋值方式，创建的对象存放到字符串对象池里，假如存在的，就不会创建；
2. new对象方式，每次都创建一个新的对象；
      
![](https://live.staticflickr.com/65535/48315050387_192d66d693_z.jpg)
     
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 21:46
 */
public class Demo3 {
    public static void main(String[] args) {
        String name1="张三";
        String name2="张三";
        String name3=new String("张三");
        String name4=new String("张三");

        System.out.println("name1==name2:"+(name1==name2));
        System.out.println("name1==name3:"+(name1==name3));
        System.out.println("name3==name4:"+(name3==name4));
    }
}
```
     
### 4. 字符串的内容不可变性
字符串的特性：不能改变字符串的内容；只能通过指向一个新的内存地址；     
      
![](https://live.staticflickr.com/65535/48314968091_7ac4026543_z.jpg)
       
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 21:51
 */
public class Demo4 {
    public static void main(String[] args) {
        String name="张";
        name+="三";
        System.out.println(name);
    }
}

```
        
### 5. String类常用方法及基本使用
1. char charAt(int index)返回指定索引处的char值。
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 22:00
 */
public class Demo5 {
    public static void main(String[] args) {
        String name="张三";
        char ming=name.charAt(1);
        System.out.println(ming);

        String srt="我是中国人";

        //遍历字符串
        for (int i=0;i<srt.length();i++){
            System.out.println(srt.charAt(i));
        }
    }
}

```
2. int length()返回此字符串的长度。
3. int indexOf() 返回指定字符在此字符中第一次出现处的索引。   
     
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 22:03
 */
public class Demo6 {
    public static void main(String[] args) {
        //indexOf方法使用示例
        String str="abcdefghdijklmnopqrstuvwxyz";
        System.out.println("d在字符串str中第一次出现的索引位置："+str.indexOf("d"));
        System.out.println("d在字符串str中第一次出现的索引位置,从索引4开始："+str.indexOf("d",4));
    }
}

```
4. String substring(int beginIndex)返回一个新的字符串，它是此字符串的一个子字符串。该子字符串从指定索引处的字符开始，直到此字符串末尾。
     
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 22:08
 */
public class Demo7 {
    public static void main(String[] args) {
        //subString方法使用
        String str="不开心每一天,不可能";
        String newStr=str.substring(1);
        String newStr2=str.substring(1,6);
        System.out.println(str);
        System.out.println(newStr);
        System.out.println(newStr2);
    }
}

```
5. String toUpperCase() 使用默认语言环境的规则将此String中的所有字符都转换为大写。
     
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 22:12
 */
public class Demo8 {
    public static void main(String[] args) {
        String str="I'm a boy!";
        String upStr=str.toUpperCase();   //转换成大写
        System.out.println("str:"+str);
        System.out.println("upStr:"+upStr);


        String lowerStr=upStr.toLowerCase();  //转换成小写
        System.out.println("lowerStr:"+lowerStr);
    }
}

```
      
6. 综合实例
编程输入一个字符串，要求去掉前后的空格，然后分别统计其中英文字母，空格，数字和其他字符的个数。
      
```java
package com.java.chap07.sec08;

/**
 * @author Yan
 * @date 2019/7/18 22:18
 */
public class Demo9 {
    public static void main(String[] args) {
        String str="  aB23 2&*  &*   s2  ";
        //去掉前面和后面的空白
        String newStr=str.trim();
        System.out.println("str:"+str);
        System.out.println("newStr:"+newStr);


        int yingWen=0;
        int kongGe=0;
        int shuZi=0;
        int qiTa=0;

        for (int i=0;i<newStr.length();i++){
            char c=newStr.charAt(i);
            if (c>='a'&&c<='z'||(c>='A'&&c<='Z')){
                //判断英文字符
                yingWen++;
                System.out.println("英文字符："+c);
            }else if (c>='0'&&c<='9'){
                //判断数字
                shuZi++;
                System.out.println("数字："+c);
            }else if (c==' '){
                //判断空格
                kongGe++;
                System.out.println("空格："+c);
            }else {
                //判断其他
                qiTa++;
                System.out.println("其他："+c);
            }
        }
        System.out.println();
        System.out.println("英文总数："+yingWen);
        System.out.println("数字总数："+shuZi);
        System.out.println("空格总数："+kongGe);
        System.out.println("其他总数："+qiTa);
    }
}
```
       
## 9. Java类的继承
1. 继承定义以及基本使用
定义：子类能够继承父类的属性和方法；      
**注意点**：Java中只支持单继承；私有方法不能继承。
       
**Animal.java**     
```java
package com.java.chap07.sec09;

/**
 * 动物类
 *
 * @author Yan
 * @date 2019/7/19 15:32
 */
public class Animal {
    //属性姓名
    private String name;
    //属性年龄
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }


    //方法say
    public void say() {
        System.out.println("我是一个动物，我叫：" + this.getName() + "我的年龄是：" + this.getAge());
    }
}

```
      
**Dog.java**      
```java
package com.java.chap07.sec09;

/**
 *
 * 定义Dog类，继承自Animal类
 * @author Yan
 * @date 2019/7/19 17:25
 */
public class Dog extends Animal{


    public static void main(String[] args) {
        Dog dog=new Dog();
        dog.setName("Pick");
        dog.setAge(1);
        dog.say();
    }
}

```
        
2. 方法重写
      
**Animal.java**     
```java
package com.java.chap07.sec09;

/**
 * 动物类
 *
 * @author Yan
 * @date 2019/7/19 15:32
 */
public class Animal {
    //属性姓名
    private String name;
    //属性年龄
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }


    //方法say
    public void say() {
        System.out.println("我是一个动物，我叫：" + this.getName() + "我的年龄是：" + this.getAge());
    }
}

```
             
**Cat.java**    
```
package com.java.chap07.sec09;

/**
 * @author Yan
 * @date 2019/7/19 17:32
 */
public class Cat extends Animal {

    /**
     * 重写父类的say方法
     */
    //方法say
    public void say() {
        System.out.println("我是一只猫，我叫：" + this.getName() + "我的年龄是：" + this.getAge());
    }

    public static void main(String[] args) {
        Cat cat=new Cat();
        cat.setName("Mini");
        cat.setAge(2);
        cat.say();
    }
}

```
3. 对象实例化过程以及super关键字
       
**Animal.java**     
```java
package com.java.chap07.sec09;

/**
 * 动物类
 *
 * @author Yan
 * @date 2019/7/19 15:32
 */
public class Animal {
    //属性姓名
    private String name;
    //属性年龄
    private int age;


    /**
     * 无参构造方法
     */
    public Animal(){
        System.out.println("无参构造方法");
    }

    /**
     * 有参父类构造方法
     * @param name 名字
     * @param age 年龄
     */
    public Animal(String name,int age){
        System.out.println("有参父类构造方法");
        this.name=name;
        this.age=age;
    }


    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }


    //方法say
    public void say() {
        System.out.println("我是一个动物，我叫：" + this.getName() + "我的年龄是：" + this.getAge());
    }
}

```

**Cat.java**         
```java
package com.java.chap07.sec09;

/**
 * @author Yan
 * @date 2019/7/19 17:32
 */
public class Cat extends Animal {


    private String address;

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }

    public Cat() {
        super();
        System.out.println("子类无参构造方法");
    }

    public Cat(String name, int age,String address) {
        super(name, age);
        this.address=address;
        System.out.println("子类有参构造方法");
    }

    /**
     * 重写父类的say方法
     */
    //方法say
    public void say() {
        //调用父类的say方法
        super.say();
        System.out.println("我是一只猫，我叫：" + this.getName() + "我的年龄是：" + this.getAge()+"我来自："+this.address);
    }

    public static void main(String[] args) {
        Cat cat=new Cat("Mini",1,"火星");
        //cat.setName("Mini");
        //cat.setAge(2);
        cat.say();
    }
}

```
       
## 10. final关键字
>使用final声明的类不能被继承
>使用final声明的方法不能被子类覆盖
>使用final声明的变量不能被修改，即为常量

1. final 修饰类
           
代码示例：   
**JiangShi.java**  
```java
package com.java.chap07.sec10;

/**
 * @author Yan
 * @date 2019/7/19 21:04
 */
public final class JiangShi {

}

```
       
**test.java**       
```java
package com.java.chap07.sec10;

/**
 * @author Yan
 * @date 2019/7/19 21:05
 */
public class Test extends JiangShi{

}

```
       
2. final 修饰方法
       
**People.java**     
```java
package com.java.chap07.sec10;

/**
 * @author Yan
 * @date 2019/7/19 21:55
 */
public class People {



    public final void action(){
        System.out.println("做一个良好公民！");
    }



}

```
       
**Test.java**        
```java
package com.java.chap07.sec10;

/**
 * @author Yan
 * @date 2019/7/19 21:05
 */
public class Test extends People{


    public void action(){
        System.out.println("做一个坏蛋");
    }
}

```
3. final 修饰的变量
      
**People.java**
```java
package com.java.chap07.sec10;

/**
 * @author Yan
 * @date 2019/7/19 21:55
 */
public class People {

    private final int a=1;

    public void action(){
        a=2;
        System.out.println("做一个良好公民！");
    }
}

```

**Common.java**
```java
package com.java.chap07.sec10;

/**
 * @author Yan
 * @date 2019/7/19 22:25
 */
public class Common {
    /**
     * 静态常量
     */
    public static final String SOMETILE="中国的首都是北京";
}

```
       
**Test.java**
```java
package com.java.chap07.sec10;

/**
 * @author Yan
 * @date 2019/7/19 21:05
 */
public class Test extends People{


    public void action(){
        System.out.println("做一个坏蛋");
    }

    public static void main(String[] args) {
        System.out.println(Common.SOMETILE);
    }
}
```
       
## 11. 抽象类
定义：在Java中，含有抽象方法的类称为抽象类，同样不能生成对象。     
**注意点**：      
1. 包含一个抽象方法的类是抽象类
2. 抽象类和抽象方法都要用abstract 关键字声明
3. 抽象方法只需要声明而不需要实现
4. 抽象类必须被子类（假如不是抽象类）必须重写抽象类中的全部抽象方法
5. 抽象类不能被实例化

       
**People.java**
      
```java
package com.java.chap07.sec11;

/**
 * 定义一个抽象类People
 * @author Yan
 * @date 2019/7/20 15:25
 */
public abstract class People {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void say(){
        System.out.println("我的姓名是："+this.getName());
    }


    /**
     *
     * 定义一个抽象方法职业
     */
    public abstract void profession();

}

```
        
**Student.java**
      
```java
package com.java.chap07.sec11;

/**
 * @author Yan
 * @date 2019/7/20 15:29
 */
public class Student extends People{
    @Override
    public void profession() {
        System.out.println("职业是：学生");
    }
}

```
         
**Teacher.java**
       
```java
package com.java.chap07.sec11;

/**
 * @author Yan
 * @date 2019/7/20 15:30
 */
public class Teacher extends People{
    @Override
    public void profession() {
        System.out.println("职业是：老师");
    }
}

```
        
**Test.java**
       
```java
package com.java.chap07.sec11;

/**
 * @author Yan
 * @date 2019/7/20 15:28
 */
public class Test {
    public static void main(String[] args) {
        //抽象类不能被实例化
        //People p=new People();
        Student student=new Student();
        student.profession();


        Teacher teacher=new Teacher();
        teacher.profession();
    }
}

```

## 12. 接口
定义：一种特殊的“抽象类”，没有普通方法，有全局常量和公共的抽象方法所组成。        
1. 接口的定义

**A.java**   
```java
package com.java.chap07.sec12;

/**
 * 定义一个接口A
 * @author Yan
 * @date 2019/7/20 15:40
 */
public interface A {


    /**
     * 全局常量
     */
    public static final String TITLE="www.baidu.com";


    /**
     * 定义一个抽象方法 abstract可以省略
     */
    public void a();
}

```
2. 实现接口
可以实现一个或者多个接口

实现一个接口       
**A.java**
        
```java
package com.java.chap07.sec12;

/**
 * 定义一个接口A
 * @author Yan
 * @date 2019/7/20 15:40
 */
public interface A {


    /**
     * 全局常量
     */
    public static final String TITLE="www.baidu.com";


    /**
     * 定义一个抽象方法 abstract可以省略
     */
    public void a();
}

```
       
**Test.java**
       
```java
package com.java.chap07.sec12;

/**
 * @author Yan
 * @date 2019/7/20 16:04
 */
public class Test implements A{
    @Override
    public void a() {
        System.out.println("a方法");
    }

    public static void main(String[] args) {
        Test test=new Test();
        test.a();
        System.out.println(Test.TITLE);
    }
}

```
       
实现多个接口       
       
**A.java**
         
```java
package com.java.chap07.sec12;

/**
 * 定义一个接口A
 * @author Yan
 * @date 2019/7/20 15:40
 */
public interface A {

    /**
     * 全局常量
     */
    public static final String TITLEA="www.baidu.com";


    /**
     * 定义一个抽象方法 abstract可以省略
     */
    public void a();
}

```
          
**B.java**
      
```java
package com.java.chap07.sec12;

/**
 * 定义一个接口A
 * @author Yan
 * @date 2019/7/20 15:40
 */
public interface B {


    /**
     * 全局常量
     */
    public static final String TITLEB="www.google.com";


    /**
     * 定义一个抽象方法 abstract可以省略
     */
    public void b();
}

```
        
**Test.java**
       
```java
package com.java.chap07.sec12;

/**
 * @author Yan
 * @date 2019/7/20 16:04
 */
public class Test implements A, B {
    @Override
    public void a() {
        System.out.println("a方法");
    }

    @Override
    public void b() {
        System.out.println("b方法");
    }

    public static void main(String[] args) {
        Test test = new Test();
        test.a();
        test.b();
        System.out.println(Test.TITLEA);
        System.out.println(Test.TITLEB);
    }


}

```
3. 继承类和实现接口
先继承，后实现接口
      
**C.java**
       
```java
package com.java.chap07.sec12;

/**
 * @author Yan
 * @date 2019/7/20 16:12
 */
public class C {
    public void c(){
        System.out.println("c方法");
    }
}

```
       
**Test.java**
      
```java
package com.java.chap07.sec12;

/**
 * @author Yan
 * @date 2019/7/20 16:04
 */
public class Test extends C implements A, B {
    @Override
    public void a() {
        System.out.println("a方法");
    }

    @Override
    public void b() {
        System.out.println("b方法");
    }

    public static void main(String[] args) {
        Test test = new Test();
        test.a();
        test.b();
        test.c();
        System.out.println(Test.TITLEA);
        System.out.println(Test.TITLEB);
    }


}
```
      
4. 接口的继承
接口可以多继承     

**D.java**

```java
package com.java.chap07.sec12;

/**
 * 定义接口D,继承A，B接口
 * @author Yan
 * @date 2019/7/20 16:15
 */
public interface D extends A,B{
    /**
     * 定义一个抽象方法 abstract可以省略
     */
    public void d();
}

```
       
**Test2.java**
      
```java
package com.java.chap07.sec12;

/**
 * @author Yan
 * @date 2019/7/20 16:04
 */
public class Test2 extends C implements D {
    @Override
    public void a() {
        System.out.println("a方法");
    }

    @Override
    public void b() {
        System.out.println("b方法");
    }

    @Override
    public void d() {
        System.out.println("d方法");
    }

    public static void main(String[] args) {
        Test2 test = new Test2();
        test.a();
        test.b();
        test.c();
        test.d();
        System.out.println(Test2.TITLEA);
        System.out.println(Test2.TITLEB);
    }


}
```
        
## 13. 对象多态性
Java中多态性体现：     
1. 方法的重载和重写；
2. 可以用父类的引用指向子类的具体实现，而且可以随时更换为其他子类的具体实现；
        
**Animal.java**
       
```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:23
 */
public class Animal {

    public void say(){
        System.out.println("我是一个动物");
    }
}
```
       
**Cat.java**
       
```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:24
 */
public class Cat extends Animal{
    public void say(){
        System.out.println("我是一个猫");
    }

}

```
      
**Dog.java**
       
```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:24
 */
public class Dog extends Animal{
    public void say(){
        System.out.println("我是一个狗");
    }

}

```
       
**Test.java**
      
```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:25
 */
public class Test {
    public static void main(String[] args) {
        /*
        Dog dog=new Dog();
        dog.say();

        Cat cat=new Cat();
        cat.say();
        */

        //父类引用指向Dog类的具体实现
        Animal animal = new Dog();
        animal.say();

        animal=new Cat();
        animal.say();
    }
}

```
对象的转型：      
向上转型：子类对象->父类对象  **安全**       
向下转型：父类对象->子类对象  **不安全**
       
向下转型     
         
```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:25
 */
public class Test {
    public static void main(String[] args) {
        /*
        Dog dog=new Dog();
        dog.say();

        Cat cat=new Cat();
        cat.say();
        */

        //父类引用指向Dog类的具体实现
        Animal animal = new Dog();
        animal.say();


        //向下转型
        Dog dog= (Dog) animal;
        dog.say();


        //向下转型2 不安全
        Cat cat= (Cat) animal;
        cat.say();


        /*animal=new Cat();
        animal.say();
         */
    }
}

```
       
**接口方式**
       
**Animal.java**

```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:23
 */
public interface Animal2 {


    public void say2();
}

```

**Dog2.java**

```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:34
 */
public class Dog2 implements Animal2{
    @Override
    public void say2() {
        System.out.println("我是一只狗");
    }
}

```

**Cat2.java**

```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:24
 */
public class Cat2 implements Animal2 {
    public void say2() {
        System.out.println("我是一个猫");
    }

}

```
        
**Test2.java**
      
```java
package com.java.chap07.sec13;

/**
 * @author Yan
 * @date 2019/7/20 16:25
 */
public class Test2 {
    public static void main(String[] args) {


        //父类引用指向Dog类的具体实现  向上转型
        Animal2 animal2 = new Dog2();
        animal2.say2();


        animal2=new Cat2();
        animal2.say2();


        //向下转型
        Dog2 dog2= (Dog2) animal2;
        dog2.say2();


        //向下转型2 不安全
        Cat2 cat2= (Cat2) animal2;
        cat2.say2();

    }
}

```
       
## 14. Object类
>Object类是所有类的父类；
        
```java
package com.java.chap07.sec14;

/**
 * @author Yan
 * @date 2019/7/20 21:02
 */
public class A extends Object{

    /**
     * Object 类是所有类的父类
     */
    public A(){
        super();
    }
}

```
         
### 1. Object类的常用方法
1.     
            
```java
public String toString();    //返回该对象的字符串表示
```

代码示例：     

```java
package com.java.chap07.sec14;

/**
 * @author Yan
 * @date 2019/7/20 21:04
 */
public class People {

    private String name;

    public People(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }


    @Override
    public String toString() {
        return this.getName();
    }

    public static void main(String[] args) {
        People people=new People("张三");
        System.out.println(people);
        System.out.println(people.toString());
    }
}

```
            
2.        
          
```java
public boolean equals(Object obj);  //指示其他某个对象是否与此对象“相等”
```
        
代码示例：     
        
```java
package com.java.chap07.sec14;

/**
 * @author Yan
 * @date 2019/7/20 21:04
 */
public class People {

    private String name;

    public People(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }


    @Override
    public String toString() {
        return this.getName();
    }

    @Override
    public boolean equals(Object obj) {
        String name=((People)obj).getName();
        System.out.println(name);
        return this.name==name;
    }

    public static void main(String[] args) {
        People people=new People("张三");
        People people1=new People("张三");
        People people3=new People("李四");
        System.out.println("people.equals(people1)"+people.equals(people1));
        System.out.println("people1.equals(people3)"+people1.equals(people3));
        System.out.println(people);
        System.out.println(people.toString());
    }
}

```
        
## 15. instanceof关键字
作用：判断一个对象是否属于一个类      
格式： 对象  instanceof类 返回布尔类型         
向下转型作判断；    
       
代码示例：     
      
**Animal.java**
      
```java
package com.java.chap07.sec15;

/**
 * @author Yan
 * @date 2019/7/20 21:17
 */
public class Animal {
    public void say(){
        System.out.println("我是一个动物");
    }
}

```
       
**Cat.java**
       
```java
package com.java.chap07.sec15;

/**
 * @author Yan
 * @date 2019/7/20 21:17
 */
public class Cat extends Animal {
    public void say(){
        System.out.println("我是一只猫");
    }


    /**
     * 子类方法
     */
    public void f2(){
        System.out.println("我喜欢吃鱼");
    }
}

```
         
**Dog.java**
      
```java
package com.java.chap07.sec15;

/**
 * @author Yan
 * @date 2019/7/20 21:17
 */
public class Dog extends Animal {
    public void say(){
        System.out.println("我是一只狗");
    }


    /**
     * 子类方法
     */
    public void f2(){
        System.out.println("我的名字是jack");
    }
}

```
       
**Test.java**
       
```java
package com.java.chap07.sec15;

/**
 * @author Yan
 * @date 2019/7/20 21:18
 */
public class Test {

    public static void doSomeThing(Animal animal){
        animal.say();
        if (animal instanceof Dog){
            ((Dog)animal).f2();
        }
        if (animal instanceof Cat){
            ((Cat)animal).f2();
        }
    }

    public static void main(String[] args) {
        Animal dog=new Dog();
        System.out.println("dog对象是否属于Animal类："+(dog instanceof Animal));
        System.out.println("dog对象是否属于Dog类："+(dog instanceof Dog));
        System.out.println("dog对象是否属于Cat类："+(dog instanceof Cat));

        doSomeThing(new Dog());
        doSomeThing(new Cat());
    }
}

```
       
## 16. 匿名内部类
作用：假如某个类只使用一次，则可以使用匿名内部类。 

代码示例：    

**A.java**

```java
package com.java.chap07.sec16;

/**
 * @author Yan
 * @date 2019/7/20 21:34
 */
public interface A {

    public void a();
}

```

**B.java**

```java
package com.java.chap07.sec16;

/**
 * @author Yan
 * @date 2019/7/20 21:35
 */
public class B implements A{
    @Override
    public void a() {
        System.out.println("只使用一次");
    }
}

```

**Test.java**

```java
package com.java.chap07.sec16;

/**
 * @author Yan
 * @date 2019/7/20 21:35
 */
public class Test {
    public void test(A a){
        a.a();
    }

    public static void main(String[] args) {
        Test test=new Test();
        test.test(new B());

        //匿名内部类
        test.test(new A() {
            @Override
            public void a() {
                System.out.println("匿名内部类，一次性使用");
            }
        });
    }
}

```
         
## 17. 包装类
每个基本类型都有一个对应的类；
      
|序号|基本类型|包装类|
|--|--|--|
|1|int|Integer|
|2|char|Character|
|3|short|Short|
|4|long|Long|
|5|float|Float|
|6|double|Double|
|7|boolean|Boolean|
|8|byte|Byte|
       
1. 装箱和拆箱
     
```java
package com.java.chap07.sec17;

/**
 * @author Yan
 * @date 2019/7/20 22:02
 */
public class Demo1 {
    public static void main(String[] args) {
        int a=1;
        Integer i=new Integer(a);    //装箱  把基本变量变成对象变量
        int b=i.intValue();   //拆箱  把对象变量变成基本变量
        System.out.println("a="+a+",i="+i+",b="+b);
    }
}

```
     
2. 自动装箱和拆箱
      
```java
package com.java.chap07.sec17;

/**
 * @author Yan
 * @date 2019/7/20 22:05
 */
public class Demo2 {
    public static void main(String[] args) {
        Integer i=1;     //自动装箱的过程  自动把基本数据转换成对象
        int i2=i;   //自动拆箱   自动把对象转换成基本数据
        System.out.println("i="+i+",i2="+i2);
    }
}

```
       
3. 包装类的作用
       
```java
package com.java.chap07.sec17;

/**
 * @author Yan
 * @date 2019/7/20 22:07
 */
public class Demo3 {
    public static void main(String[] args) {
        String a="1";
        String b="2";

        int m=Integer.parseInt(a);
        int n=Integer.parseInt(b);
        System.out.println("a+b="+(m+n));
    }
}

```
         
## 18. 设计模式
1. 单例模式
在Java应用中，单例对象能保证在一个JVM中，该对象只有一个实例存在。
              
饿汉式     
       
**Singleton1.java**
        
```java
package com.java.chap07.sec18;

/**
 * @author Yan
 * @date 2019/7/21 14:05
 */
public class Singleton1 {

    /**
     * 构造方法私有
     */
    private Singleton1(){

    }

    /**
     * 饿汉式单例实现
     */
    private static final Singleton1 single1=new Singleton1();


    /**
     * 静态工厂方式
     */
    public static Singleton1 getInstance(){
        return single1;
    }
}

```

**TestSingleton.java**

```java
package com.java.chap07.sec18;

/**
 * @author Yan
 * @date 2019/7/21 14:06
 */
public class TestSingleton {
    public static void main(String[] args) {
        //Singleton1 singleton1=new Singleton1();

        Singleton1 singleton1=Singleton1.getInstance();
        Singleton1 singleton2=Singleton1.getInstance();

        System.out.println("饿汉式："+(singleton1==singleton2));

        TestSingleton testSingleton=new TestSingleton();
        TestSingleton testSingleton2=new TestSingleton();
        System.out.println(testSingleton==testSingleton2);
    }
}

```

 
懒汉式      

**Singleton2.java**

```java
package com.java.chap07.sec18;

/**
 * @author Yan
 * @date 2019/7/21 14:05
 */
public class Singleton2 {

    /**
     * 构造方法私有
     */
    private Singleton2(){

    }

    /**
     * 懒汉式单例实现    在第一次调用的时候实例化
     */
    private static Singleton2 single;

    /**
     * 工厂
     */
    public synchronized static Singleton2 getInstance(){
        if (single==null){
            //第一次调用的时候实例化
            System.out.println("第一次调用的时候实例化");
            single=new Singleton2();
        }
        return single;
    }
}

```

**TestSingleton.java**

```java
package com.java.chap07.sec18;

/**
 * @author Yan
 * @date 2019/7/21 14:06
 */
public class TestSingleton {
    public static void main(String[] args) {
        Singleton2 singleton3=Singleton2.getInstance();
        Singleton2 singleton4=Singleton2.getInstance();
        System.out.println("懒汉式："+(singleton3==singleton4));
    }
}
```

# Java异常处理
## 异常的概念
      
代码示例：     
      
```java
package com.java.chap08.sec01;

/**
 * @author Yan
 * @date 2019/7/21 14:30
 */
public class ExceptionDemo {
    public static void main(String[] args) {
        String str="123a";
        int a=Integer.parseInt(str);
        System.out.println(a);
    }
}

```
## 捕获和处理异常
在Java中，我们用try...catch...来捕获异常；   

```java
try...catch...finally
```
        
代码示例：     
      
```java
package com.java.chap08.sec02;

/**
 * @author Yan
 * @date 2019/7/21 14:32
 */
public class Demo1 {
    public static void main(String[] args) {
        String str="123a";
        try {
            int a=Integer.parseInt(str);
        }catch (NumberFormatException e){
            e.printStackTrace();
        }

        
        System.out.println("aaaa");
    }

}
```
      
```java
package com.java.chap08.sec02;

/**
 * @author Yan
 * @date 2019/7/21 15:59
 */
public class Demo2 {

    public static void testFinally(){
        String str="123a";
        try{
            int a=Integer.parseInt(str);
            System.out.println(a);
        }catch (Exception e){
            e.printStackTrace();
            System.out.println("exception");
            return;
        }finally {
            System.out.println("final end");
        }
        System.out.println("end");
    }

    public static void main(String[] args) {
        testFinally();
    }
}

```
## throws和throw关键字
throws表示当前方法不处理异常，而是交给方法的调用处去处理。       
throw表示直接抛出一个异常
        
代码示例：      
      
**throws**
       
```java
package com.java.chap08.sec03;

/**
 * @author Yan
 * @date 2019/7/21 16:03
 */
public class Demo1 {
    /**
     * 把异常向外抛
     * @throws NumberFormatException
     */
    public static void testThrows() throws NumberFormatException {
        String str = "123a";
        int a = Integer.parseInt(str);
        System.out.println(a);
    }


    public static void main(String[] args) {
        try {

            testThrows();
        }catch (Exception e){
            System.out.println("在这里处理异常");
            e.printStackTrace();
        }
        System.out.println("I'm here");
    }
}

```
         
**throw**
        
```java
package com.java.chap08.sec03;

/**
 * @author Yan
 * @date 2019/7/21 16:07
 */
public class Demo2 {

    public static void testThrow(int a) throws Exception{
        if (a==1){

            //直接抛出一个异常类
            throw new Exception("有异常");

        }
        System.out.println(a);
    }

    public static void main(String[] args) {
        try {
            testThrow(1);
        } catch (Exception e) {
            e.printStackTrace();
        }

        try {
            testThrow(0);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```
## Exception和RuntimeException区别
Exception 是检查型异常，例如Exception在程序中必须使用try...catch进行处理；

RuntimeException 是非检查型异常，例如NumberFormatException，可以不使用try...catch进行处理，但是如果产生异常，则异常将由JVM进行处理；       

RuntimeException 最好也用try...catch捕获。

代码示例：     
          
```java
package com.java.chap08.sec04;

/**
 * @author Yan
 * @date 2019/7/21 16:12
 */
public class Demo1 {

    /**
     * 运行时异常，编译时不检查，可以不适用try...catch捕获
     * @throws RuntimeException
     */
    public static void testRuntimeException() throws RuntimeException {
        throw new RuntimeException("运行时异常");
    }

    /**
     * Exception异常，编译时异常，必须使用try...catch捕获
     * @throws Exception
     */
    public static void testException() throws Exception{
        throw new Exception("Exception异常");
    }

    public static void main(String[] args) {
        try{
            testRuntimeException();

        }catch (Exception e){
            e.printStackTrace();
        }
        try {
            testException();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```
       
## 自定义异常类
代码示例：    
      
**CustomerException.java**
       
```java
package com.java.chap08.sec05;

/**
 * 自定义异常，继承自Exception
 * @author Yan
 * @date 2019/7/21 16:18
 */
public class CustomerException extends Exception{


    public CustomerException(String message){
        super(message);
    }



}

```
       
**TestCustomerException.java**
       
```java
package com.java.chap08.sec05;

/**
 * @author Yan
 * @date 2019/7/21 16:19
 */
public class TestCustomerException {

    public static void test() throws CustomerException{
        throw new CustomerException("自定义异常");
    }

    public static void main(String[] args) {
        try {
            test();
        } catch (CustomerException e) {
            e.printStackTrace();
        }
    }
}

```
        
# Java常用类
## Java日期处理类
1. Date类
      
```java
package com.java.chap09.sec01;

import java.util.Date;

/**
 * 日期类Date
 * @author Yan
 * @date 2019/7/21 20:56
 */
public class TestDate {
    public static void main(String[] args) {
        Date date=new Date();
        System.out.println("当前日期："+date);
    }
}

```
       
2. Calendar类
       
```java
package com.java.chap09.sec01;

        import java.util.Calendar;

/**
 * @author Yan
 * @date 2019/7/21 20:58
 */
public class TestCalendar {
    public static void main(String[] args) {
        Calendar calendar = Calendar.getInstance();
        System.out.println(calendar.get(Calendar.YEAR));
        System.out.println(calendar.get(Calendar.MONTH) + 1);
        System.out.println("现在是" + calendar.get(Calendar.YEAR) + "年"
                + (calendar.get(Calendar.MONTH) + 1) + "月"
                + calendar.get(Calendar.DAY_OF_MONTH) + "日"
                + calendar.get(Calendar.HOUR_OF_DAY) + "时"
                + calendar.get(Calendar.MINUTE) + "分"
                + calendar.get(Calendar.SECOND) + "秒");
    }
}

```
     
3. SimpleDateFormat
      
```java
package com.java.chap09.sec01;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

/**
 * @author Yan
 * @date 2019/7/21 21:05
 */
public class TestSimpleDateFormat {

    /**
     * 将日期对象格式为指定格式的日期字符串
     * @param date 传入的日期对象
     * @param format  格式
     * @return
     */
    public static String formatDate(Date date,String format){
        String result="";
        SimpleDateFormat sdf=new SimpleDateFormat(format);
        if (date!=null){
            result=sdf.format(date);
        }
        return result;
    }

    /**
     * 将日期字符串转换成一个日期对象
     * @param dataStr 日期字符串
     * @param format 格式
     * @return
     */
    public static Date formatDate(String dataStr,String format) throws ParseException {
        SimpleDateFormat sdf=new SimpleDateFormat(format);

        return sdf.parse(dataStr);
    }

    public static void main(String[] args) throws ParseException {
        Date date=new Date();
        //SimpleDateFormat sdf=new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        //System.out.println(sdf.format(date));

        String dataStr="2010-07-21 21:12:26";
        Date date1=formatDate(dataStr,"yyyy-MM-dd HH:mm:ss");

        System.out.println(formatDate(date,"yyyy-MM-dd HH:mm:ss"));


        System.out.println(formatDate(date1,"yyyy-MM-dd HH:mm:ss"));
    }
}

```
        
## String VS StringBuffer
String：对String类型的对象操作，等同于重新生成一个对象，然后将引用指向它；
       
StringBuffer：对StringBuffer类型的对象操作，操作的始终是用一个对象。     
        
1. String
       
![](https://live.staticflickr.com/65535/48344498272_fa4a07241c_z.jpg)
        
代码示例：      
     
```java
package com.java.chap09.sec02;

/**
 * @author Yan
 * @date 2019/7/22 14:00
 */
public class TestString {
    public static void main(String[] args) {
        String str="123";
        str+="abc";
        System.out.println(str);
    }
}

```
         
2. StringBuffer
       
![](https://live.staticflickr.com/65535/48344384271_961416d201_z.jpg)
       
代码示例：     
       
```java
package com.java.chap09.sec02;

/**
 * @author Yan
 * @date 2019/7/22 14:01
 */
public class TestStringBuffer {
    public static void main(String[] args) {
        StringBuffer sb=new StringBuffer("123");
        sb.append("abc");
        System.out.println(sb);
    }
}

```
       
## Math类
>1. max方法：求最大值
>2. min方法：求最小值
>3. round方法：四舍五入
>4. pow方法：求次幂
       
代码示例：     
      
```java
package com.java.chap09.sec03;

/**
 * @author Yan
 * @date 2019/7/22 14:10
 */
public class TestMath {
    public static void main(String[] args) {
        System.out.println("最大值："+Math.max(1,2));
        System.out.println("最小值："+Math.min(1,2));
        System.out.println("四舍五入："+Math.round(12.4));
        System.out.println("次幂："+Math.pow(3,4));
    }
}

```
          
## Arrays类
>1. toString()方法：返回指定数组内容的字符串表示形式
>2. sort()方法：对指定的类型数组按数字升序进行排序
>3. binarySearch()方法：使用二分搜索法来搜索指定类型数组，以获得指定的值
>4. fill()方法：将指定类型值分配给指定类型数组的每个元素
       
代码示例：      
      
```java
package com.java.chap09.sec04;

import java.util.Arrays;

/**
 * @author Yan
 * @date 2019/7/22 14:36
 */
public class TestArrays {
    public static void main(String[] args) {
        int arr[]={1,7,3,8,2};
        System.out.println("以字符串形式输出数组："+Arrays.toString(arr));

        Arrays.sort(arr);   //给数组排序
        System.out.println("排序后的数组"+Arrays.toString(arr));

        System.out.println(Arrays.binarySearch(arr,7));

        Arrays.fill(arr,0);   //将指定内容填充到数组中
        System.out.println("填充数组后的字符串："+Arrays.toString(arr));
    }
}
```
         
# Java泛型
## 泛型引入
定义：使用泛型可以指代任意对象类型
      
代码示例：     
       
**C1.java**
       
```java
package com.java.chap10.sec01;

/**
 * @author Yan
 * @date 2019/7/22 16:00
 */
public class C1 {
    private Integer a;

    public C1(Integer a) {
        super();
        this.a = a;
    }

    public Integer getA() {
        return a;
    }

    public void setA(Integer a) {
        this.a = a;
    }


    /**
     * 打印a的类型
     */
    public void print(){
        System.out.println("a的类型是："+a.getClass().getName());
    }
}

```

**C2.java**
                     
```java
package com.java.chap10.sec01;

/**
 * @author Yan
 * @date 2019/7/22 16:02
 */
public class C2 {
    private String a;

    public C2(String a) {
        super();
        this.a = a;
    }

    public String getA() {
        return a;
    }

    public void setA(String a) {
        this.a = a;
    }

    /**
     * 打印a的类型
     */
    public void print(){
        System.out.println("a的类型是："+a.getClass().getName());
    }
}

```
       
**C12.java**
       
```java
package com.java.chap10.sec01;

/**
 * @author Yan
 * @date 2019/7/22 16:09
 */
public class C12 {
    private Object object;

    public C12(Object object) {
        super();
        this.object = object;
    }

    public Object getObject() {
        return object;
    }

    public void setObject(Object object) {
        this.object = object;
    }

    /**
     * 打印object的类型
     */
    public void print(){
        System.out.println("a的类型是："+object.getClass().getName());
    }
}

```
         
**CC.java**
       
```java
package com.java.chap10.sec01;

/**
 * 定义泛型类
 * @author Yan
 * @date 2019/7/24 15:56
 */
public class CC<T> {

    private T ob;

    public CC(T ob) {
        super();
        this.ob = ob;
    }

    public T getOb() {
        return ob;
    }

    public void setOb(T ob) {
        this.ob = ob;
    }


    /**
     * 打印T的类型
     */
    public void print(){
        System.out.println("T的实际类型"+ob.getClass().getName());;
    }
}

```
       
**Test.java**
      
```java
package com.java.chap10.sec01;

/**
 * @author Yan
 * @date 2019/7/22 16:03
 */
public class Test1 {

    public static void main(String[] args) {
        //begin test c1
        C1 c1=new C1(1);
        c1.print();

        int i=c1.getA();
        System.out.println("i="+i);

        //end test c1

        //begin test c2
        C2 c2=new C2("Hi");
        c2.print();
        String s1=c2.getA();
        System.out.println("s1="+s1);
        //end test c2


        //begin test c12
        C12 c12=new C12(1);   //向上转型
        c12.print();
        int i12= (Integer) c12.getObject();   //向下转型
        System.out.println("i12="+i12);

        C12 c121=new C12("你好");  //向上转型
        c121.print();
        String i121=(String) c121.getObject();  //向下转型
        System.out.println("i121="+i121);
        //end test c12


        //begin test CC
        CC<Integer> cc=new CC<Integer>(1);
        cc.print();
        int icc=cc.getOb();
        System.out.println("icc="+icc);
        //end test CC

        //begin test CC
        CC<String> cc1=new CC<String>("你好");
        cc1.print();
        String icc1=cc1.getOb();
        System.out.println("icc1="+icc1);
        //end test CC
    }
}

```
## 限制泛型
       
代码示例：     
     
**Animal.java**
       
```java
package com.java.chap10.sec02;

/**
 * @author Yan
 * @date 2019/7/24 16:07
 */
public class Animal {
    public void print(){
        System.out.println("动物");
    }
}

```
      
**Cat.java**
      
```
package com.java.chap10.sec02;

/**
 * @author Yan
 * @date 2019/7/24 16:07
 */
public class Cat extends Animal{
    public void print(){
        System.out.println("Cat");
    }
}

```
      
**Dog.java**
      
```java
package com.java.chap10.sec02;

/**
 * @author Yan
 * @date 2019/7/24 16:07
 */
public class Dog extends Animal{
    public void print(){
        System.out.println("Dog");
    }
}


```
        
**Demo.java**
      
```java
package com.java.chap10.sec02;

/**
 * @author Yan
 * @date 2019/7/24 16:08
 */

public class Demo <T extends Animal>{
    private T ob;

    public Demo(T ob) {
        super();
        this.ob = ob;
    }

    public T getOb() {
        return ob;
    }

    public void setOb(T ob) {
        this.ob = ob;
    }

    public void print(){
        System.out.println("T的类型是： "+ob.getClass().getName());
    }
}

```
       
**Test.java**
      
```java
package com.java.chap10.sec02;

/**
 * @author Yan
 * @date 2019/7/24 16:11
 */
public class Test {
    public static void main(String[] args) {
        Demo<Dog> demo=new Demo<Dog>(new Dog());
        Dog dog=demo.getOb();
        dog.print();

        Demo<Cat> demo2=new Demo<Cat>(new Cat());
        Cat cat=demo2.getOb();
        cat.print();


        //Demo<Integer> demo3=new Demo<Integer>(2);
        Demo<Animal> demo3=new Demo<Animal>(new Animal());
    }
}

```
## 通配符泛型
       
代码示例：     
     
**Test.java**
       
```java
package com.java.chap10.sec03;

import com.java.chap10.sec02.Animal;
import com.java.chap10.sec02.Cat;
import com.java.chap10.sec02.Demo;
import com.java.chap10.sec02.Dog;

/**
 * @author Yan
 * @date 2019/7/24 16:23
 */
public class Test {

    /**
     * 通配符泛型
     * @param animal
     */
    private static void take(Demo<?> animal){
        animal.print();
    }
    public static void main(String[] args) {
        Demo<Dog> dog=new Demo<Dog>(new Dog());
        take(dog);

        Demo<Cat> cat=new Demo<Cat>(new Cat());
        take(cat);

        Demo<Animal> animalDemo=new Demo<Animal>(new Animal());
        take(animalDemo);
    }
}

```
       
## 泛型方法
       
代码示例：     
     
```java
package com.java.chap10.sec04;

/**
 * @author Yan
 * @date 2019/7/24 19:39
 */
public class Test {


    /**
     * 泛型方法
     * @param t
     * @param <T>
     */
    public static <T> void f(T t){
        System.out.println("T的类型是："+t.getClass().getName());
    }
    public static void main(String[] args) {
        f("");
        f(1);
        f(1.0);
        f(new Object());
    }
}

```
       
# Java集合
## Java集合的引入
      
代码示例：      
           
**Student.java**
       
```java
package com.java.chap11.sec01;

/**
 * @author Yan
 * @date 2019/7/25 14:40
 */
public class Student {

    private String name;
    private int age;

    public Student(String name, int age) {
        super();
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

```
       
**Demo.java**
      
```java
package com.java.chap11.sec01;

import java.util.LinkedList;

/**
 * @author Yan
 * @date 2019/7/25 14:41
 */
public class Demo {

    public static void main(String[] args) {
        Student student[]=new Student[3];
        Student student1=new Student("张三",1);
        Student student2=new Student("李四",3);
        Student student3=new Student("王五",4);


        LinkedList<Student> list=new LinkedList<Student>();
        list.add(student1);
        list.add(student2);
        list.add(student3);


        /**
         * 遍历集合
         */
        for (int i=0;i<list.size();i++){
            Student student4=list.get(i);
            System.out.println(student4.getName()+":"+student4.getAge());
        }
    }
}

```
            
## List集合
是Collection接口的子接口，也是最常用的接口。此接口对Collection接口进行了大量的扩展，List集合里的元素是允许重复的。      
       
1. ArrayList实现类
       
代码实现：    
      
```java
package com.java.chap11.sec02;

import java.util.ArrayList;

/**
 * @author Yan
 * @date 2019/7/25 15:09
 */
public class TestArrayList {
    public static void printArrayList(ArrayList<String> arrayList){
        System.out.println("当前的集合元素");
        for (int i=0;i<arrayList.size();i++){
            System.out.print(arrayList.get(i)+" ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        ArrayList<String> arrayList=new ArrayList<String>();
        //添加元素
        arrayList.add("张三");
        arrayList.add("李四");

        printArrayList(arrayList);

        //将指定的元素插入此列表中的指定位置
        arrayList.add(1,"小张三");
        printArrayList(arrayList);

        //用指定的元素替代此列表指定位置上的元素
        arrayList.set(2,"小李四");
        printArrayList(arrayList);

        //移除此列表中指定位上的元素
        arrayList.remove(0);
        printArrayList(arrayList);
    }
}

```
2. LinkedList实现类
      
代码示例：    
     
```java
package com.java.chap11.sec02;

import java.util.LinkedList;

/**
 * @author Yan
 * @date 2019/7/25 15:36
 */
public class TestLinkedList {

    public static void printLinkedList(LinkedList<String> linkedList){
        System.out.println("当前元素集合：");
        for (int i=0;i<linkedList.size();i++){
            System.out.print(linkedList.get(i)+"  ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        LinkedList<String> linkedList=new LinkedList<String>();
        linkedList.add("张三");
        linkedList.add("李四");
        linkedList.add("王五");
        linkedList.add("李四");
        linkedList.add("赵六");

        printLinkedList(linkedList);

        //返回此列表中首次出现的指定元素的索引，如果此列表中不包括该元素，则返回-1；
        System.out.println(linkedList.indexOf("李四"));

        //获取但不移除此列表的第一个元素；如果此列表为空，则返回null
        System.out.println(linkedList.peekFirst());
        printLinkedList(linkedList);

        //获取但不移除此列表的最后一个元素；如果此列表为空，则返回null
        System.out.println(linkedList.peekLast());
        printLinkedList(linkedList);

        //获取并移除此列表的第一个元素；如果此列表为空，则返回null
        System.out.println(linkedList.pollFirst());
        printLinkedList(linkedList);

        //获取并移除此列表的最后一个元素；如果此列表为空，则返回null
        System.out.println(linkedList.pollLast());
        printLinkedList(linkedList);
    }
}

```
        
## 集合的遍历
1. Iterator
      
代码示例：     
      
```java
package com.java.chap11.sec03;

import com.java.chap11.sec01.Student;

import java.util.Iterator;
import java.util.LinkedList;

/**
 * @author Yan
 * @date 2019/7/25 15:51
 */
public class TestIterator {

    public static void main(String[] args) {
        LinkedList<Student> list=new LinkedList<Student>();
        list.add(new Student("张三",10));
        list.add(new Student("李四",20));
        list.add(new Student("王五",30));


        /**
         * 用Iterator遍历集合
         */
        Iterator<Student> iterator=list.iterator();   //返回一个迭代器
        while(iterator.hasNext()){
            Student s=iterator.next();    //返回迭代的下一个元素
            System.out.println("姓名："+s.getName()+"   年龄："+s.getAge());
        }

    }
}

```
        
2. foreach
      
代码示例：     
     
```java
package com.java.chap11.sec03;

import com.java.chap11.sec01.Student;

import java.util.Iterator;
import java.util.LinkedList;

/**
 * @author Yan
 * @date 2019/7/25 15:57
 */
public class TestForeach {
    public static void main(String[] args) {
        LinkedList<Student> list=new LinkedList<Student>();
        list.add(new Student("张三",10));
        list.add(new Student("李四",20));
        list.add(new Student("王五",30));


        /**
         * 用Foreach遍历集合
         */
        for (Student s:list){
            System.out.println("姓名："+s.getName()+"   年龄："+s.getAge());

        }

    }
}

```
       
## Set集合
是Collertion接口的子接口，没有对Collection接口进行扩展，里面不允许存重复的内容。     
       
1. HashSet类
        
代码示例：     
     
```java
package com.java.chap11.sec04;

import java.util.HashSet;
import java.util.Iterator;

/**
 * @author Yan
 * @date 2019/7/25 16:02
 */
public class TestHashSet {

    public static void main(String[] args) {
        /**
         * 1. HashSet是无序的
         * 2. 不允许有重复值
         */
        HashSet<String> hashSet=new HashSet<String>();
        hashSet.add("1");
        hashSet.add("2");
        hashSet.add("5");
        hashSet.add("4");
        hashSet.add("2");

        /**
         * 用Iterator遍历集合
         */
        Iterator<String> iterator=hashSet.iterator();
        while (iterator.hasNext()){
            String s=iterator.next();
            System.out.println(s+" ");
        }


    }
}

```

## Map集合
是存放一对值的最大接口，即接口中的每一个元素都是一对，以key->value键值对的形式保存。     
      
1. HashMap类
      
代码示例：     
        
```java
package com.java.chap11.sec05;

import com.java.chap11.sec01.Student;

import java.util.HashMap;
import java.util.Iterator;

/**
 * @author Yan
 * @date 2019/7/25 16:08
 */
public class TestHashMap {
    public static void main(String[] args) {
        HashMap<String, Student> hashMap=new HashMap<String,Student>();
        hashMap.put("1号",new Student("张三",10));
        hashMap.put("2号",new Student("李四",20));
        hashMap.put("3号",new Student("王五",30));

        // 通过key获取value
        Student student=hashMap.get("1号");
        System.out.println(student.getName()+":"+student.getAge());

        Iterator<String> iterator=hashMap.keySet().iterator();  //获取key的集合，再获取迭代器
        while (iterator.hasNext()){
            String key=iterator.next();    //获取key
            Student student1=hashMap.get(key);   //通过key获取value
            System.out.println("key="+key+"value=["+student1.getName()+","+student1.getAge()+"]");
        }
    }
}

```
      
# Java多线程
## 多线程的引入
定义：同时对多项任务加以控制
      
代码示例：     
      
**Demo.java**
      
```java
package com.java.chap12.sec01;

/**
 * @author Yan
 * @date 2019/7/27 13:15
 */
public class Demo1 {

    /**
     * 听音乐
     */
    private static void music(){
        for (int i=0;i<1000;i++){
            System.out.println("听音乐");
        }
    }

    /**
     * 吃饭
     *
     */
    private static void eat(){
        for (int i=0;i<1000;i++){
            System.out.println("吃饭");
        }
    }
    public static void main(String[] args) {
        //music();
        //eat();

        /**
         * 利用多线程实现一边吃饭一边听歌
         */
        Music musicThread=new Music();
        Eat eatThread=new Eat();
        musicThread.start();
        eatThread.start();
    }
}

```
       
**Eat.java**
      
```java
package com.java.chap12.sec01;

/**
 * @author Yan
 * @date 2019/7/27 13:18
 */
public class Eat extends Thread {
    @Override
    public void run() {
        for (int i=0;i<1000;i++){
            try {
                Thread.sleep(100);
                System.out.println("吃饭");
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

```
       
**Music.java**
      
```java
package com.java.chap12.sec01;

/**
 * @author Yan
 * @date 2019/7/27 13:19
 */
public class Music extends Thread {
    @Override
    public void run() {
        for (int i=0;i<1000;i++){
            try {
                Thread.sleep(100);
                System.out.println("听音乐");
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

```
        
## Java多线程实现
1. 继承Thread类
       
代码示例：     
     
```java
package com.java.chap12.sec02;

/**
 * @author Yan
 * @date 2019/7/27 13:24
 */
public class Thread1 extends Thread {


    private int baoZi=1;
    private String threadName;

    public Thread1(String threadName) {
        super();
        this.threadName = threadName;
    }

    @Override
    public synchronized void run() {
        while (baoZi<=10){
            System.out.println(threadName+"吃第"+baoZi+"包子");
            baoZi++;
        }
    }

    public static void main(String[] args) {
        System.out.println("张三，李四一起吃包子，每人吃了10个");
        Thread1 t1=new Thread1("张三线程");
        Thread1 t2=new Thread1("李四线程");
        t1.start();
        t2.start();
    }
}

```
      
2. 实现Runnable接口
      
代码示例：    
     
```java
package com.java.chap12.sec02;

/**
 * @author Yan
 * @date 2019/7/27 13:29
 */
public class Thread2 implements Runnable {
    private int baoZi=1;
    private String threadName;

    public Thread2(String threadName) {
        super();
        this.threadName = threadName;
    }

    @Override
    public synchronized void run() {
        while (baoZi<=10){
            System.out.println(threadName+"吃第"+baoZi+"包子");
            baoZi++;
        }
    }

    public static void main(String[] args) {
        //System.out.println("张三，李四一起吃包子，每人吃了10个");
        //Thread2 t1=new Thread2("张三线程");
        //Thread2 t2=new Thread2("李四线程");
        //Thread t11=new Thread(t1);
        //Thread t12=new Thread(t2);
        //t11.start();
        //t12.start();

        Thread2 t1=new Thread2("超级张三线程");
        Thread t11=new Thread(t1);
        Thread t12=new Thread(t1);
        Thread t13=new Thread(t1);
        Thread t14=new Thread(t1);
        //实现资源共享
        t11.start();
        t12.start();
        t13.start();
        t14.start();
    }
}

```
      
## 线程状态
      
![](https://live.staticflickr.com/65535/48385151952_855767c53c_z.jpg)
      
>1. 创建状态
在程序中用构造方法创建了一个线程对象后，新的线程对象便处于新建状态，此时，它已经有了相应的内存空间和其他资源，但还处于不可运行状态。新建一个线程对象可采用Thread类的构造方法来实现，例如，“Thread thread=new Thread();”。
      
>2. 就绪状态
新建线程对象后，调用该线程的start()方法就可以启动线程。当线程启动时，线程进入就绪状态。此时，线程将进入线程队列排队，等待CPU服务，这表明它已经具备了运行条件。
        
>3. 运行状态
当就绪状态的线程被调用并获得处理器资源时，线程就进入了运行状态。此时，自动调用该线程对象的run()方法。run()方法定义了该线程的操作和功能。
       
>4. 堵塞状态
一个正在运行的线程在某些特殊情况下，如被人为挂起或需要执行耗时的输入/输出操作时，将让出CPU并暂时中止自己的执行，进入堵塞状态，堵塞时，线程不能进入排队队列，只有当引起堵塞的原因被消除后，线程才可以转入就绪状态。
        
>5. 死亡状态
线程调用stop()方法时或run()方法执行结束后，即处于死亡状态。处于死亡状态的线程不具有继续运行的能力。
         
## 线程常用方法
1. getName(); 返回该线程的名称。
2. currentThread(); 返回对当前正在执行的线程对象的引用。
3. isAlive(); 测试线程是否处于活动状态。
4. sleep(); 线程休眠。
5. setPriority(int newPriority); 更改线程的优先级。
6. yield(); 暂停当前正在执行的线程对象，并执行其他线程。

代码示例：     
           
**getName()、currentThread()**
      
```java
package com.java.chap12.sec04;

import javax.swing.plaf.TableHeaderUI;

/**
 * @author Yan
 * @date 2019/7/27 14:23
 */
public class Demo1 implements Runnable{

    @Override
    public void run() {
        for (int i=0;i<10;i++){
            //获取当前线程
            Thread t=Thread.currentThread();
            System.out.println(t.getName()+":"+i);  //返回线程的名称
        }
    }


    public static void main(String[] args) {
        Demo1 demo1=new Demo1();
        new Thread(demo1).start();
        new Thread(demo1).start();
        new Thread(demo1,"线程3").start();
    }
}

```
        
**isAlive()**
      
```java
package com.java.chap12.sec04;

/**
 * @author Yan
 * @date 2019/7/27 14:35
 */
public class Demo2 implements Runnable{
    @Override
    public void run() {
        for (int i=0;i<10;i++){
            //获取当前线程
            Thread t=Thread.currentThread();
            System.out.println(t.getName()+":"+i);  //返回线程的名称
        }
    }

    public static void main(String[] args) {
        Demo2 demo2=new Demo2();
        Thread t1=new Thread(demo2);
        System.out.println("t1是否活动："+t1.isAlive());
        t1.start();
        System.out.println("t1是否活动："+t1.isAlive());
    }
}

```
       
**sleep()**
     
```java
package com.java.chap12.sec04;

/**
 * @author Yan
 * @date 2019/7/27 14:35
 */
public class Demo3 implements Runnable{
    @Override
    public void run() {
        for (int i=0;i<10;i++){
            try {
                Thread.sleep(1000);
                //获取当前线程
                Thread t=Thread.currentThread();
                System.out.println(t.getName()+":"+i);  //返回线程的名称
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }

    public static void main(String[] args) {
        Demo3 demo2=new Demo3();
        Thread t1=new Thread(demo2);
        t1.start();
    }
}
```
       
**setPriority(int newPriority)**
     
```java
package com.java.chap12.sec04;

/**
 * @author Yan
 * @date 2019/7/27 14:35
 */
public class Demo4 implements Runnable{
    @Override
    public void run() {
        for (int i=0;i<10;i++){
            try {
                Thread.sleep(1000);
                //获取当前线程
                Thread t=Thread.currentThread();
                System.out.println(t.getName()+":"+i);  //返回线程的名称
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }

    public static void main(String[] args) {
        Demo4 demo4=new Demo4();
        Thread t1=new Thread(demo4,"线程A");
        Thread t2=new Thread(demo4,"线程B");
        Thread t3=new Thread(demo4,"线程C");
        t1.setPriority(Thread.MAX_PRIORITY);
        t2.setPriority(Thread.MIN_PRIORITY);
        t3.setPriority(Thread.NORM_PRIORITY);
        t1.start();
        t2.start();
        t3.start();
    }
}

```
       
**yield()**
       
```java
package com.java.chap12.sec04;

/**
 * @author Yan
 * @date 2019/7/27 14:35
 */
public class Demo5 implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            try {
                Thread.sleep(1000);
                //获取当前线程
                Thread t = Thread.currentThread();
                System.out.println(t.getName() + ":" + i);  //返回线程的名称
                if (i==5){
                    System.out.println("线程礼让");
                    Thread.currentThread().yield();
                }
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }

    public static void main(String[] args) {
        Demo5 demo5 = new Demo5();
        new Thread(demo5, "线程A").start();
        new Thread(demo5, "线程B").start();

    }
}

```
          
## 线程同步
1. 同步方法
       
2. 同步锁
      
代码示例：     
     
**Demo2.java**
     
```java
package com.java.chap12.sec05;

/**
 * @author Yan
 * @date 2019/7/27 14:54
 */
public class Demo2 implements Runnable {

    private int baoZi=10;

    /**
     * 同步方法
     */
    @Override
    public synchronized void run() {
        while (baoZi>0){
            System.out.println(Thread.currentThread().getName()+"吃了第"+baoZi+"包子");
            baoZi--;
        }
    }


    public static void main(String[] args) {
        Demo2 demo1=new Demo2();
        new Thread(demo1,"张三").start();
        new Thread(demo1,"李四").start();
        new Thread(demo1,"王五").start();
    }
}

```
      
**Demo3.java**
      
```java
package com.java.chap12.sec05;

/**
 * @author Yan
 * @date 2019/7/27 14:54
 */
public class Demo3 implements Runnable {

    private int baoZi = 10;

    @Override
    public void run() {
        /**
         * 同步块
         */
        synchronized (this) {
            while (baoZi > 0) {
                System.out.println(Thread.currentThread().getName() + "吃了第" + baoZi + "包子");
                baoZi--;
            }

        }
    }


    public static void main(String[] args) {
        Demo3 demo1 = new Demo3();
        new Thread(demo1, "张三").start();
        new Thread(demo1, "李四").start();
        new Thread(demo1, "王五").start();
    }
}

```
       
# Java图形界面Swing框架
## Swing简介
1. Swing是Java的一个图形框架，继承自AWT；
2. Swing主要涉及到容器，组件，还有布局管理器；
3. Swing与用户交互的时候还涉及到事件概念
       
## JFrame容器
1. public void setVisible(boolean b):根据参数b的值显示或隐藏此窗体
     
2. public void setSize(int width,int height):调整组件的大小，使其宽度为width，高度为height
             
3. public void setLocation(int x,.int y):将组件移到新位置。通过此组件父级坐标空间中的x和y参数来指定新位置的左上角
                  
4. public Container getContentPane():返回此窗体的contentPane对象
       
5. public void setBackground(Color c):设置组件的背景色
       
代码示例：     
      
```java
package com.java.chap13.sec02;

import javax.swing.*;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/27 15:38
 */
public class JFrameTest {
    public static void main(String[] args) {
        JFrame jFrame=new JFrame("JFrame窗体");
        /*Container c=jFrame.getContentPane();
        c.setBackground(Color.blue);*/
        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300,200);   //设置容器的位置
        jFrame.setSize(500,500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
    }
}

```
      
## JButton组件
      
代码示例：     
      
```java
package com.java.chap13.sec03;

import javax.swing.*;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/27 16:18
 */
public class JButtonTest {

    public static void main(String[] args) {
        JFrame jFrame=new JFrame("JButton测试");
        JButton jButton=new JButton("这是一个按钮");
        jFrame.add(jButton);


        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300,200);   //设置容器的位置
        jFrame.setSize(500,500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }

}

```
       
## Swing布局管理器
1. FlowLayout流式布局
使用此种布局方式会使所有的组件像流水一样依次进行排列
      
代码示例：     
      
```java
package com.java.chap13.sec04;

import javax.swing.*;
import java.awt.*;

/**
 * FlowLayout流式布局
 * @author Yan
 * @date 2019/7/27 16:26
 */
public class FlowLayout {
    public static void main(String[] args) {
        JFrame jFrame=new JFrame("FlowLayout测试");

        //jFrame.setLayout(new java.awt.FlowLayout());
        //jFrame.setLayout(new java.awt.FlowLayout(java.awt.FlowLayout.LEFT));
        jFrame.setLayout(new java.awt.FlowLayout(java.awt.FlowLayout.LEFT,15,15));
        JButton jButton=null;
        for(int i=0;i<9;i++){
            jButton=new JButton("JButton"+i);
            jFrame.add(jButton);
        }

        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300,200);   //设置容器的位置
        jFrame.setSize(500,500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
        
2. BorderLayout
使用此种布局方式将一个窗体的版面划分成东、西、南、北、中5个区域，可以直接将需要的组件放到这5个区域中
       
代码示例：     
       
```java
package com.java.chap13.sec04;

import javax.swing.*;
import java.awt.*;

/**
 *
 * @author Yan
 * @date 2019/7/28 15:35
 */
public class BorderLayoutTest {
    public static void main(String[] args) {
        JFrame jFrame=new JFrame("BorderLayout测试");


        //jFrame.setLayout(new BorderLayout());
        jFrame.setLayout(new BorderLayout(5,5));
        jFrame.add(new JButton("东"),BorderLayout.EAST);
        jFrame.add(new JButton("西"),BorderLayout.WEST);
        jFrame.add(new JButton("南"),BorderLayout.SOUTH);
        jFrame.add(new JButton("北"),BorderLayout.NORTH);
        jFrame.add(new JButton("中"),BorderLayout.CENTER);


        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300,200);   //设置容器的位置
        jFrame.setSize(500,500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
         
3. GridLayout表格布局
使用此种布局是以表格的形式进行布局管理的，在使用此布局管理器时必须设置显示的行数和列数
       
代码示例：      
       
```java
package com.java.chap13.sec04;

import javax.swing.*;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/28 15:39
 */
public class GridLayoutTest {
    public static void main(String[] args) {
        JFrame jFrame=new JFrame("GridLayout测试");


        jFrame.setLayout(new GridLayout(4,5,5,5));
        JButton jButton=null;
        for (int i=0;i<19;i++){
            jButton=new JButton("JButton"+i);
            jFrame.add(jButton);
        }


        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300,200);   //设置容器的位置
        jFrame.setSize(500,500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
       
4. 绝对布局
       
代码示例：     
      
```java
package com.java.chap13.sec04;

import javax.swing.*;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/28 15:44
 */
public class AbsoluteLayoutTest {
    public static void main(String[] args) {
        JFrame jFrame=new JFrame("绝对布局测试");

        jFrame.setLayout(null);
        JButton jButton1=new JButton("按钮1");
        JButton jButton2=new JButton("按钮2");
        jFrame.add(jButton1);
        jFrame.add(jButton2);
        jButton1.setBounds(50,10,100,20);
        jButton2.setBounds(70,40,200,30);


        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300,200);   //设置容器的位置
        jFrame.setSize(500,500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
          
## JLable 组件
     
代码示例：    
      
```java
package com.java.chap13.sec05;

import javax.swing.*;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/28 16:02
 */
public class JLableTest {
    public static void main(String[] args) {
        JFrame jFrame=new JFrame("JLable测试");

        JLabel jLabel=new JLabel("JLable组件",JLabel.CENTER);
        jFrame.add(jLabel);
        

        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300,200);   //设置容器的位置
        jFrame.setSize(500,500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
       
## 文本框组件
1. JTextField 文本框
      
代码示例：     
      
```java
package com.java.chap13.sec06;

import javax.swing.*;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/28 16:17
 */
public class JTextFiledTest {
    public static void main(String[] args) {
        JFrame jFrame=new JFrame("JTextFiled单行文本框测试");

        jFrame.setLayout(new GridLayout(1,2,10,10));
        JLabel jLabel=new JLabel("用户名：");
        JTextField jTextField=new JTextField();
        jFrame.add(jLabel);
        jFrame.add(jTextField);

        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300,200);   //设置容器的位置
        jFrame.setSize(500,500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
       
2. JPasswordField 密码框
      
代码示例：      
     
```java
package com.java.chap13.sec06;

import javax.swing.*;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/28 16:42
 */
public class JPasswordFiledTest {
    public static void main(String[] args) {
        JFrame jFrame = new JFrame("JPasswordFiled密码框测试");

        jFrame.setLayout(new GridLayout(2, 2, 10, 10));
        JLabel jLabel = new JLabel("用户名：");
        JTextField jTextField = new JTextField();
        JLabel jLabe2 = new JLabel("密码：");
        JPasswordField jPasswordField=new JPasswordField();
        jFrame.add(jLabel);
        jFrame.add(jTextField);
        jFrame.add(jLabe2);
        jFrame.add(jPasswordField);

        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300, 200);   //设置容器的位置
        jFrame.setSize(500, 500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
       
3. JTextArea 文本域
       
代码示例：     
       
```java
package com.java.chap13.sec06;

import javax.swing.*;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/28 16:17
 */
public class JTextAreaTest {
    public static void main(String[] args) {
        JFrame jFrame = new JFrame("JTextArea文本域测试");

        jFrame.setLayout(new GridLayout(1, 2, 10, 10));
        JLabel jLabel = new JLabel("描述：");
        JTextArea jTextArea = new JTextArea();
        jFrame.add(jLabel);
        jFrame.add(jTextArea);

        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300, 200);   //设置容器的位置
        jFrame.setSize(500, 500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
        
## JPanel 轻量级容器
代码示例：     
      
```java
package com.java.chap13.sec07;

import javax.swing.*;
import javax.swing.border.EmptyBorder;
import java.awt.*;

/**
 * @author Yan
 * @date 2019/7/28 16:50
 */
public class JPanelTest {
    public static void main(String[] args) {
        JFrame jFrame = new JFrame("JPanel面板测试");

        JPanel jPanel=new JPanel();
        jPanel.setLayout(new GridLayout(3,2,10,10));
        jFrame.add(jPanel);
        jPanel.setBorder(new EmptyBorder(10,10,10,10));   //设置边距


        JLabel jLabel = new JLabel("用户名：");
        JTextField jTextField = new JTextField();
        JLabel jLabe2 = new JLabel("密码：");
        JPasswordField jPasswordField = new JPasswordField();
        JButton jButton=new JButton("登录");
        JButton jButton2=new JButton("重置");

        jPanel.add(jLabel);
        jPanel.add(jTextField);
        jPanel.add(jLabe2);
        jPanel.add(jPasswordField);
        jPanel.add(jButton);
        jPanel.add(jButton2);

        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300, 200);   //设置容器的位置
        jFrame.setSize(500, 500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
       
## Swing事件处理
      
代码示例：     
      
**demo1**
        
```java
package com.java.chap13.sec08;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

/**
 * @author Yan
 * @date 2019/7/28 22:11
 */

class JButtonListener implements ActionListener{
    @Override
    public void actionPerformed(ActionEvent e) {
        System.out.println(e.getActionCommand());
        JOptionPane.showMessageDialog(null,"我被点击了");
    }
}

public class EventTest1 {
    public static void main(String[] args) {
        JFrame jFrame = new JFrame("Swing事件");
        JButton jButton=new JButton("我是一个按钮");

        JButtonListener jButtonListener=new JButtonListener();
        jButton.addActionListener(jButtonListener);  //添加/注册事件监听

        jFrame.add(jButton);


        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300, 200);   //设置容器的位置
        jFrame.setSize(500, 500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
       
**demo2**
       
```java
package com.java.chap13.sec08;

import javax.swing.*;
import java.awt.*;
import java.awt.event.WindowEvent;
import java.awt.event.WindowListener;

/**
 * @author Yan
 * @date 2019/7/28 22:17
 */

//class MyWindowListener implements WindowListener {
//
//    @Override
//    public void windowOpened(WindowEvent e) {
//        System.out.println("窗口被打开");
//    }
//
//    @Override
//    public void windowClosing(WindowEvent e) {
//        System.out.println("窗口关闭");
//    }
//
//    @Override
//    public void windowClosed(WindowEvent e) {
//        System.out.println("窗口被关闭");
//    }
//
//    @Override
//    public void windowIconified(WindowEvent e) {
//        System.out.println("窗口最小化");
//    }
//
//    @Override
//    public void windowDeiconified(WindowEvent e) {
//        System.out.println("窗口从最小化恢复");
//    }
//
//    @Override
//    public void windowActivated(WindowEvent e) {
//        System.out.println("窗口被选中");
//    }
//
//    @Override
//    public void windowDeactivated(WindowEvent e) {
//        System.out.println("窗口选中被取消");
//    }
//}

public class EventTest2 {
    public static void main(String[] args) {
        JFrame jFrame = new JFrame("Swing事件");

        //MyWindowListener myWindowListener=new MyWindowListener();
        //jFrame.addWindowListener(myWindowListener);

        jFrame.addWindowListener(new WindowListener() {
            @Override
            public void windowOpened(WindowEvent e) {
                System.out.println("窗口被打开");
            }

            @Override
            public void windowClosing(WindowEvent e) {
                System.out.println("窗口关闭");
            }

            @Override
            public void windowClosed(WindowEvent e) {
                System.out.println("窗口被关闭");
            }

            @Override
            public void windowIconified(WindowEvent e) {
                System.out.println("窗口最小化");
            }

            @Override
            public void windowDeiconified(WindowEvent e) {
                System.out.println("窗口从最小化恢复");
            }

            @Override
            public void windowActivated(WindowEvent e) {
                System.out.println("窗口被选中");
            }

            @Override
            public void windowDeactivated(WindowEvent e) {
                System.out.println("窗口选中被取消");
            }
        });

        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300, 200);   //设置容器的位置
        jFrame.setSize(500, 500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
         
**demo3**
       
```java
package com.java.chap13.sec08;

import javax.swing.*;
import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;


/**
 * @author Yan
 * @date 2019/7/28 22:24
 */

//class MyWindowAdapter extends WindowAdapter{
//    @Override
//    public void windowClosing(WindowEvent e) {
//        super.windowClosing(e);
//        System.out.println("窗口关闭。。。。。。。");
//    }
//}

public class EventTest3 {
    public static void main(String[] args) {
        JFrame jFrame = new JFrame("Swing事件");

        //MyWindowAdapter myWindowAdapter=new MyWindowAdapter();
        //jFrame.addWindowListener(myWindowAdapter);


        jFrame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                super.windowClosing(e);
                System.out.println("窗口关闭。。。。");
            }
        });

        jFrame.getContentPane().setBackground(Color.red);   //设置容器的背景颜色
        jFrame.setLocation(300, 200);   //设置容器的位置
        jFrame.setSize(500, 500);    //设置容器大小
        jFrame.setVisible(true);  //让容器显示
        jFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}

```
        
# Java IO流
## IO流简介
流是一组有顺序的，有起点和终点的字节集合，是对数据传输的总称或抽象。即数据再两设备间的传输称为流，流的本质是数据传输，根据数据传输特性将流抽象为各种类，方便更直观的进行数据操作。
         
![](https://live.staticflickr.com/65535/48411733786_ac1f14f1b1_b.jpg)
        
>IO 流的分类
根据处理数据类型的不同分类：字符流和字节流
根据数据流向不同分为：输入流和输出流
      
## 文件操作File类
1. public boolean mkdir()：创建此抽象路径名指定的目录
2. public boolean createNewFile():创建一个文件
3. public boolean delete():删除此抽象路径名表示的文件或目录。如果此路径名表示一个目录，则该目录必须为空才能删除
4. public boolean exists():测试此抽象路径名表示的文件或目录是否存在
5. public File[] listFiles():返回一个抽象路径名数组，这些路径名表示此抽象路径名表示的目录中的文件
6. public boolean idDirectory():测试此抽象路径名表示的文件是否是一个目录

代码示例：     

**Demo1.java**

```java
package com.java.chap14.sec02;

import java.io.File;
import java.io.IOException;

/**
 * @author Yan
 * @date 2019/7/30 15:43
 */
public class Demo1 {
    public static void main(String[] args) throws IOException {
        File file=new File("D://java创建的目录");
        boolean b=file.mkdir();   //创建虚拟目录
        if (b){
            System.out.println("目录创建成功");
            file=new File("D://java创建的目录//java创建的文件.txt");
            boolean b2=file.createNewFile();   //创建文件
            if (b2){
                System.out.println("文件创建成功");
            }else {
                System.out.println("文件创建失败");
            }

        }else {
            System.out.println("目录创建失败");
        }
    }
}

```
       
**Demo2.java**
      
```java
package com.java.chap14.sec02;

import java.io.File;
import java.io.IOException;

/**
 * @author Yan
 * @date 2019/7/30 15:43
 */
public class Demo2 {
    public static void main(String[] args) throws IOException {
        File file=new File("D://java创建的目录//Java创建的文件.txt");
        if (file.exists()){  //假如目录存在
            boolean b=file.delete();    //删除文件
            if (b){
                System.out.println("删除文件成功");
            }else {
                System.out.println("删除文件失败");
            }
        }
        file=new File("D://java创建的目录");
        if (file.exists()){
            boolean b2=file.delete();   //删除目录
            if (b2){
                System.out.println("删除目录成功");
            }else {
                System.out.println("删除目录失败");
            }
        }
    }
}

```
       
**Demo3.java**
      
```java
package com.java.chap14.sec02;

import java.io.File;

/**
 * @author Yan
 * @date 2019/7/30 17:21
 */
public class Demo3 {
    public static void main(String[] args) {
        File file=new File("D://图书");
        File files[]=file.listFiles();    //遍历目录
        for (int i=0;i<files.length;i++){
            System.out.println(files[i]);
        }
    }
}

```
        
**Demo4.java**
       
```java
package com.java.chap14.sec02;

import java.io.File;

/**
 * @author Yan
 * @date 2019/7/30 17:45
 */
public class Demo4 {

    /**
     * 打印文件
     * @param file
     */
    public static void listFile(File file) {
        if (file != null) {
            if (file.isDirectory()) {  //是目录
                File files[]=file.listFiles();   //遍历目录
                if (files!=null){
                    for (int i=0;i<files.length;i++){
                        listFile(files[i]);   //递归调用
                    }
                }
            } else {    //是文件
                System.out.println(file);    //是文件，直接打印文件的路径
            }
        }
    }

    public static void main(String[] args) {
        File file=new File("D://实验报告");
        listFile(file);
    }
}

```
       
## 字节输入，输出流
1. InputStream 读取文件
      
代码示例：    

**Demo1.java** 
```java
package com.java.chap14.sec03;

import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

/**
 * @author Yan
 * @date 2019/7/31 14:36
 */
public class Demo1 {

    public static void main(String[] args) throws Exception {
        File file=new File("D://测试文件.txt");
        InputStream inputStream=new FileInputStream(file);   //实例化FileInputStream
        byte b[]=new byte[1024];
        int len=inputStream.read(b);
        inputStream.read(b);
        inputStream.close();   //关闭输出流
        System.out.println("读取的内容："+new String(b,0,len));
    }
}

```
       
**Demo2.java**
       
```java
package com.java.chap14.sec03;

import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

/**
 * @author Yan
 * @date 2019/7/31 14:36
 */
public class Demo2 {

    public static void main(String[] args) throws Exception {
        File file=new File("D://测试文件.txt");
        InputStream inputStream=new FileInputStream(file);   //实例化FileInputStream
        int fileLength= (int) file.length();
        byte b[]=new byte[fileLength];
        int len=inputStream.read(b);
        inputStream.read(b);
        inputStream.close();   //关闭输出流
        System.out.println("读取的内容："+new String(b));
    }
}

```
      
**Demo3.java**
       
```java
package com.java.chap14.sec03;

import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

/**
 * @author Yan
 * @date 2019/7/31 14:36
 */
public class Demo3 {

    public static void main(String[] args) throws Exception {
        File file=new File("D://测试文件.txt");
        InputStream inputStream=new FileInputStream(file);   //实例化FileInputStream
        int fileLength= (int) file.length();
        byte b[]=new byte[fileLength];
        int temp=0;
        int len=0;
        while ((temp=inputStream.read())!=-1){
            //一个字节一个字节读取，放到b字节数组里
            b[len++]= (byte) temp;
        }
        inputStream.close();   //关闭输出流
        System.out.println("读取的内容："+new String(b));
    }
}

```
        

2. OutputStream 写入文件
     
代码示例：     
       
**Demo4.java**
        
```java
package com.java.chap14.sec03;

import java.io.File;
import java.io.FileOutputStream;
import java.io.OutputStream;

/**
 * @author Yan
 * @date 2019/7/31 15:38
 */
public class Demo4 {
    public static void main(String[] args) throws Exception {
        File file=new File("D://测试文件.txt");
        OutputStream outputStream=new FileOutputStream(file);
        String str="你好，我好，大家好";
        byte b[]=str.getBytes();
        outputStream.write(b);   //将b字节数组写入到输出流中
        outputStream.close();   //关闭输出流
    }
}

```
       
**Demo5.java**
       
```java
package com.java.chap14.sec03;

import java.io.File;
import java.io.FileOutputStream;
import java.io.OutputStream;

/**
 * @author Yan
 * @date 2019/7/31 15:38
 */
public class Demo5 {
    public static void main(String[] args) throws Exception {
        File file=new File("D://测试文件.txt");
        OutputStream outputStream=new FileOutputStream(file,true);  //true追加
        String str="你好，我好，大家好";
        byte b[]=str.getBytes();
        outputStream.write(b);   //将b字节数组写入到输出流中
        outputStream.close();   //关闭输出流
    }
}

```
        
3. BufferedInputStream和BufferedOutputStream
      
代码示例：    
     
```java
package com.java.chap14.sec03;

import java.io.*;

/**
 * @author Yan
 * @date 2019/7/31 22:31
 */
public class Demo6 {

    /**
     * 缓冲
     *
     * @throws Exception
     */
    public static void bufferStream() throws Exception {
        //定义一个带缓冲的字节输入流
        BufferedInputStream bufferedInputStream = new BufferedInputStream(new FileInputStream("D://实验报告//android//Android应用开发实验指导书.doc"));
        //定义一个带缓冲的字节输出流
        BufferedOutputStream bufferedOutputStream = new BufferedOutputStream(new FileOutputStream("D://复制的文件2.doc"));
        int b = 0;
        Long startTime = System.currentTimeMillis();  //开始时间
        while ((b = bufferedInputStream.read()) != -1) {
            bufferedOutputStream.write(b);
        }
        bufferedInputStream.close();
        bufferedOutputStream.close();
        Long endTime = System.currentTimeMillis();   //结束时间
        System.out.println("缓冲花费的时间：" + (endTime - startTime));
    }


    /**
     * 非缓冲
     *
     * @throws Exception
     */
    public static void stream() throws Exception {
        InputStream inputStream = new FileInputStream("D://实验报告//android//Android应用开发实验指导书.doc");  //定义一个输入流
        OutputStream outputStream = new FileOutputStream("D://复制的文件.doc");
        int b = 0;
        Long startTime = System.currentTimeMillis();  //开始时间
        while ((b = inputStream.read()) != -1) {
            outputStream.write(b);
        }
        inputStream.close();
        outputStream.close();
        Long endTime = System.currentTimeMillis();   //结束时间
        System.out.println("非缓冲花费的时间：" + (endTime - startTime));
    }

    public static void main(String[] args) throws Exception {
        stream();

        bufferStream();
    }
}

```
4. 缓冲和非缓冲的区别及性能对比
       
## 字符输入、输出流
1. Reader读取文件
      
代码示例：    
      
**Demo1.java**
```java
package com.java.chap14.sec04;

import java.io.File;
import java.io.FileReader;
import java.io.Reader;

/**
 * @author Yan
 * @date 2019/7/31 23:00
 */
public class Demo1 {
    public static void main(String[] args) throws Exception {
        File file = new File("D://测试文件.txt");
        Reader reader=new FileReader(file);
        char c[]=new char[1024];   //字符数组
        int len=reader.read(c);
        reader.close();   //关闭输入流
        System.out.println("读取的内容是："+new String(c,0,len));
    }
}

```
        
**Demo2.java**
       
```java
package com.java.chap14.sec04;

import java.io.File;
import java.io.FileReader;
import java.io.Reader;

/**
 * @author Yan
 * @date 2019/7/31 23:04
 */
public class Demo2 {
    public static void main(String[] args) throws Exception {
        File file = new File("D://测试文件.txt");
        Reader reader=new FileReader(file);
        char c[]=new char[1024];   //字符数组
        int temp=0;
        int len=0;
        while ((temp=reader.read())!=-1){
            c[len++]= (char) temp;
        }
        reader.close();   //关闭输入流
        System.out.println("读取的内容是："+new String(c,0,len));
    }
}

```
      
2. Writer写入文件
       
代码示例：     
      
**Demo3.java**
```java
package com.java.chap14.sec04;


import java.io.*;

/**
 * @author Yan
 * @date 2019/7/31 23:06
 */
public class Demo3 {
    public static void main(String[] args) throws Exception {
        File file = new File("D://测试文件.txt");
        Writer out = new FileWriter(file);
        String str = "我爱中华";
        out.write(str);   //将字符串写入输出流
        out.close();   //关闭输出流
    }
}

```
        
**Demo4.java**
       
```java
package com.java.chap14.sec04;


import java.io.File;
import java.io.FileWriter;
import java.io.Writer;

/**
 * @author Yan
 * @date 2019/7/31 23:06
 */
public class Demo4 {
    public static void main(String[] args) throws Exception {
        File file = new File("D://测试文件.txt");
        Writer out = new FileWriter(file,true);
        String str = "我爱中华";
        out.write(str);   //将字符串写入输出流
        out.close();   //关闭输出流
    }
}

```
        
### 待续
       
# 参考
- [Java知识分享网](http://www.java1234.com/)
- [Java入门到精通-基础篇](https://www.bilibili.com/video/av45829913)
