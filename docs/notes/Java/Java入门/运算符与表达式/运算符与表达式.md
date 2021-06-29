# 1. Java运算符与表达式
![](https://live.staticflickr.com/65535/48287869506_1ed621abc2_z.jpg)
       
##  1.1. 赋值运算符
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
     
## 1.2. 算数运算符
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
      
## 1.3. 自增与自减运算符
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
       
## 1.4. 逻辑运算符
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
       
## 1.5. 关系运算符
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
     
## 1.6. 三目运算符
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
       