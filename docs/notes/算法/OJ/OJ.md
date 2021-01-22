# 1. A+B Problem
>输入：Input two integer A and B,Process to the end of the file.(Watch the Sample Input)        
>输出：For each case,output A + B in one line.(Watch the Sample Output)
        
```html
样例：
输入样例：
1 1
输出样例：
2
```
      
```java
import java.util.Scanner;

public class Demo {
    public static void main(String[] args) {
        Scanner scanner=new Scanner(System.in);
        while (scanner.hasNextInt()){
            int a=scanner.nextInt();
            int b=scanner.nextInt();
            System.out.println(a+b);
        }
    }
}
```
       
# 2. Words
>题目描述：每个句子由多个单词组成，句子中的每个单词的长度都不一样，我们假设每个单词的长度Ni为该单词的重量，你需要做的就是给出整个句子的平均重量V。     
>输入：输入只有一行，包含一个字符串S（长度不会超过100），代表整个句子，句子中只包含大小写的英文字母，每个单词之间有一个空格。      
>输出：输出句子S的平均重量V（四舍五入保留两位小数）。
       
```html
输入样例1
Who Love Solo
输出样例1
3.67
```
        
```java
package OJ.Words;

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner=new Scanner(System.in);
        String inputString=scanner.nextLine();
        String stringArr[]=inputString.split(" ");
        double length=0;
        for (int i=0;i<stringArr.length;i++){
            double l=stringArr[i].length();
            length=length+l;
        }
        double result=length/stringArr.length;
        System.out.println(String.format("%.2f",result));
    }
}
```