# 1. Java选择与循环语句
## 1.1. 程序的选择结构
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
       
## 1.2. 程序的循环结构
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
      
## 1.3. 循环结构的控制
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
      