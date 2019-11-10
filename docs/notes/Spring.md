# 相关文档与源代码
- [视频](https://www.bilibili.com/video/av47952931)
- [文档](https://github.com/yanxin152133/notes/blob/master/docs/notes/Spring.md)
- [代码](https://github.com/yanxin152133/Spring)
            
# Spring的概述
## Spring是什么
>Spring是分层的Java SE/EE应用full-stack轻量级开源框架，以IOC（Inverse Of Control：反转控制）和AOP(Aspect Oriented Programming：面向切面编程)为内核，提供了展现层Spring MVC和持久层Spring JDBC以及业务层事务管理等众多的企业级应用技术，还能整合开源世界众多著名的第三方框架和类库，逐渐成为使用最多的Java EE企业应用开源框架。
       
## Spring的发展历程
- 1997年IBM提出EJB的思想
- 1998年，SUN指定开发标准规范EJB1.0
- 1999年，EJB1.1发布
- 2001年，EJB2.0发布
- 2003年，EJB2.1发布
- 2006年，EJB3.0发布
- Rob Johnson(Spring之父)        
    Expert One-to-One J2EE Design and Development(2002)       
    阐述了J2EE使用EJB开发设计的有点及解决方案      
    Expert One-to-One J2EE Development without EJB(2004)     
    阐述了J2EE开发不适用EJB的解决方式（Spring雏形）
            
- 2017年9月份发布了Spring的最新版本Spring5.0通用版（GA）

## Spring的优势
- 方便解耦，简化开发      
    通过Spring提供的IOC容器，可以将对象间的恶意来关系交由  Spring进行控制，避免硬编码所造成的过度程序耦合。用户也不必再为单例模式类、属性文件解析等这些很底层的需求编写代码，可以更专注于上层的应用。

- AOP编程的支持     
    通过Spring的AOP功能，方便进行面向切面的编程，许多不容易用传统OOP实现的功能可以通过AOP轻松应付。
       
- 声明式事务的支持      
    可以将我们从单调烦闷的事务管理代码中解脱出来，通过声明式方式灵活的进行事务的管理，提高开发效率和质量。
         
- 方便程序的测试         
    可以使用非容器依赖的编程方式进行几乎所有的测试工作，测试不再是昂贵的操作，而是随手可做的事情。
              
- 方便集成各种优秀的框架        
    Spring可以降低各种框架的使用难度，提供了对各种优秀框架（Struts、Hibernate、Hessian、Quartz等）的直接支持。
        
- 降低JavaEE API的使用难度        
    Spring对JavaEE API（如JDBC、JavaMail、远程调用等）进行了薄薄的封装层，使用这些API的使用难度大为降低。
         
- Java源码是经典学习范例       
    Spring的源代码设计精妙、结构清晰、匠心独用，处处体现着大师对Java设计模式灵活运用以及对Java技术的高深造诣。它的源代码无意是Java技术的最佳实践的范例。
          
## Spring体系结构
       
![](../pict/spring-overview.png)
        
# 程序的耦合及解耦
## 什么是程序的耦合
>耦合性(Coupling)，也叫耦合度，是对程序间关联程度的度量。耦合的强弱取决于模块间接口的复杂性、调用模块的方式以及通过界面传送数据的多少。模块间的耦合度是指模块间的依赖关系，包括控制关系、调用关系、数据传递关系。模块间联系越多，其耦合性越强，同时表明其独立性越差（降低耦合性，可以提高其独立性）。耦合性存在于各个领域，而非软件设计中独有的，但是本文只讨论软件工程中的耦合。
在软件工程中，耦合指的就是对象之间的依赖性。对象之间的耦合度越高，维护成本越高。因此对象的设计应使类和构件之间的耦合最小。软件设计中通常用耦合度和内聚度作为衡量模块独立程度的标注。划分模块的一个准则就是高内聚低耦合。
它有如下分类：       
（1）内容耦合：一个模块直接修改或操作另一个模块的数据，或一个模块不通过正常入口而转入另一个模块。内容耦合是最高程度的耦合，应该避免使用之。     
（2）公共耦合：两个或两个以上的模块共同引用一个全局数据项。在具有大量公共耦合的结构中，确定究竟是哪个模块给全局变量赋了一个特定的值是非常困难的。       
（3）外部耦合：一组模块都访问同一全局简单变量而不是同一全局数据结构，而且不是通过参数传递该全局变量的信息。     
（4）控制耦合：一个模块通过接口向另一模块传递一个控制信号，接受信号的模块根据信号值而进行适当的动作。       
（5）标记耦合：若一个模块A通过接口向两个模块B和C传递一个公共参数，则称模块B和C之间存在一个标记耦合。       
（6）数据耦合：模块之间通过参数来传递数据。数据耦合是最低的一种耦合形式，系统中一般都存在这种类型的耦合，因为为了完成一些有意义的功能，往往需要将某些模块的输出数据作为另一模块的输入数据。        
（7）非直接耦合：两个模块之间没有直接的关系，它们之间的联系完全是通过主模块的控制和调用来实现的。        

总结：
耦合是影响软件复杂度和设计质量的一个重要因素，在设计上我们应采用一下原则：如何模块间必须存在耦合，就尽量使用数据耦合，少用控制耦合，限制公共耦合的范围，尽量避免使用内容耦合。

内聚与耦合
内聚标志一个模块内各个元素彼此结合的紧密程度，它是信息隐蔽和局部话概念的自然拓展。内聚是从功能角度来度量模块内的联系，一个好的内聚模块应当恰好做一件事情。它描述的是模块内的功能联系。耦合是软件结构中各模块之间相互连接的一种度量，耦合强弱取决于模块间接口的复杂度、进入或访问一个模块的点以及通过接口的数据。程序讲究的是低耦合、高内聚。就是同一个模块内的各个元素之间要高度紧密，但是各个模块之间的相互依存度却不要那么紧密。
内聚和耦合是密切相关的，同其他模块存在高耦合意味着低内聚，而高内聚的模块意味着该模块同其他模块之间是低耦合。在软件设计中，应力争做到高内聚，低耦合
                
## 编写jdbc的工程代码用于分析程序的耦合
1. pom.xml
        
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.spring</groupId>
    <artifactId>day01</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>

    <dependencies>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.6</version>
        </dependency>
    </dependencies>
</project>
```
       
2. JdbcDemo1.java
         
```java
package com.spring.jdbc;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

/**
 * 程序的耦合
 *      耦合：程序间的依赖关系
 *          包括：
 *              类之间的依赖
 *              方法间的依赖
 *      解耦：
 *          降低程序间的依赖关系
 *      实际开发中：
 *          应该做到：编译器不依赖，运行时才依赖
 *      解耦的思路：
 *          第一步：使用反射来创建对象，而避免使用new关键字
 *          第二步：通过读取配置文件来获取要创建的对象全限定类名
 *          
 */
public class jdbcDemo {
    public static void main(String[] args) throws Exception {
        //1.注册驱动
        //DriverManager.registerDriver(new com.mysql.jdbc.Driver());
        Class.forName("com.mysql.jdbc.Driver");
        //2.获取连接
        Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/spring", "root", "root");
        //3.获取操作数据库的预处理对象
        PreparedStatement pstm = conn.prepareStatement("select * from account");
        //4.执行SQL，得到结果集
        ResultSet rs = pstm.executeQuery();
        //5.遍历结果集
        while (rs.next()) {
            System.out.println(rs.getString("name"));
        }
        //6.释放资源
        rs.close();
        pstm.close();
        conn.close();
    }
}

```
         
3. sql.sql
        
```sql
create table account(
    id int primary key auto_increment,
    name varchar(40),
    money float
)character set utf8 collate utf8_general_ci;

insert into account(name, money) values ('aaa',1000);
insert into account(name, money) values ('bbb',1000);
insert into account(name, money) values ('ccc',1000);
```
       
## 工厂模式解耦
# IOC概念和Spring中的IOC
## Spring中基于XML的IOC环境搭建
# 依赖注入（Dependency Injection）