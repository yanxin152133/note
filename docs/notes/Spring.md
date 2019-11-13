# 相关文档与源代码
- [视频](https://www.bilibili.com/video/av47952931)
- [文档](https://github.com/yanxin152133/notes/blob/master/docs/notes/Spring.md)
- [代码](https://github.com/yanxin152133/Spring)
            
# Spring的概述
## Spring是什么
>Spring是分层的Java SE/EE应用full-stack轻量级开源框架，以IOC（Inverse Of Control：反转控制）和AOP(Aspect Oriented Programming：面向切面编程)为内核，提供了展现层Spring MVC和持久层Spring JDBC以及业务层事务管理等众多的企业级应用技术，还能整合开源世界众多著名的第三方框架和类库，逐渐成为使用最多的Java EE企业应用开源框架。
         
### 依赖注入
Spring 最认同的技术是控制反转的依赖注入（DI）模式。控制反转（IoC）是一个通用的概念，它可以用许多不同的方式去表达，依赖注入仅仅是控制反转的一个具体的例子。
            
当编写一个复杂的 Java 应用程序时，应用程序类应该尽可能的独立于其他的 Java 类来增加这些类可重用可能性，当进行单元测试时，可以使它们独立于其他类进行测试。依赖注入（或者有时被称为配线）有助于将这些类粘合在一起，并且在同一时间让它们保持独立。
                   
到底什么是依赖注入？让我们将这两个词分开来看一看。这里将依赖关系部分转化为两个类之间的关联。例如，类 A 依赖于类 B。现在，让我们看一看第二部分，注入。所有这一切都意味着类 B 将通过 IoC 被注入到类 A 中。
                         
依赖注入可以以向构造函数传递参数的方式发生，或者通过使用 setter 方法 post-construction。由于依赖注入是 Spring 框架的核心部分，所以我将在一个单独的章节中利用很好的例子去解释这一概念。
       
### 面向方面的程序设计（AOP）
Spring 框架的一个关键组件是面向切面的程序设计（AOP）框架。一个程序中跨越多个点的功能被称为横切关注点，这些横切关注点在概念上独立于应用程序的业务逻辑。有各种各样常见的很好的关于方面的例子，比如日志记录、声明性事务、安全性，和缓存等等。
            
在 OOP 中模块化的关键单元是类，而在 AOP 中模块化的关键单元是切面。AOP 帮助你将横切关注点从它们所影响的对象中分离出来，然而依赖注入帮助你将你的应用程序对象从彼此中分离出来。
             
Spring 框架的 AOP 模块提供了面向切面的程序设计实现，可以定义诸如方法拦截器和切入点等，从而使实现功能的代码彻底的解耦出来。使用源码级的元数据，可以用类似于.Net属性的方式合并行为信息到代码中。
               
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
          
## 使用Spring框架的好处
下面列出的是使用 Spring 框架主要的好处：
           
- Spring 可以使开发人员使用 POJOs 开发企业级的应用程序。只使用 POJOs 的好处是你不需要一个 EJB 容器产品，比如一个应用程序服务器，但是你可以选择使用一个健壮的 servlet 容器，比如 Tomcat 或者一些商业产品。
        
- Spring 在一个单元模式中是有组织的。即使包和类的数量非常大，你只要担心你需要的，而其它的就可以忽略了。
          
- Spring 不会让你白费力气做重复工作，它真正的利用了一些现有的技术，像ORM 框架、日志框架、JEE、Quartz 和 JDK 计时器，其他视图技术。
         
- 测试一个用 Spring 编写的应用程序很容易，因为环境相关的代码被移动到这个框架中。此外，通过使用 JavaBean-style POJOs，它在使用依赖注入注入测试数据时变得更容易。
         
- Spring 的 web 框架是一个设计良好的 web MVC 框架，它为比如 Structs 或者其他工程上的或者不怎么受欢迎的 web 框架提供了一个很好的供替代的选择。MVC模式导致应用程序的不同方面(输入逻辑，业务逻辑和UI逻辑)分离，同时提供这些元素之间的松散耦合。      
    - 模型(Model)封装了应用程序数据，通常它们将由POJO类组成。
    - 视图(View)负责渲染模型数据，一般来说它生成客户端浏览器可以解释HTML输出。
    - 控制器(Controller)负责处理用户请求并构建适当的模型，并将其传递给视图进行渲染。
         
         
- Spring 对JavaEE开发中非常难用的一些API（JDBC、JavaMail、远程调用等），都提供了封装，使这些API应用难度大大降低。
        
- 轻量级的 IOC 容器往往是轻量级的，例如，特别是当与 EJB 容器相比的时候。这有利于在内存和 CPU 资源有限的计算机上开发和部署应用程序。
        
- Spring提供了一致的事务管理接口，可向下扩展到（使用一个单一的数据库，例如）本地事务并扩展到全局事务（例如，使用 JTA）。
          
## Spring体系结构
       
![](../pict/spring-overview.png)
        
### 核心容器
核心容器由spring-core，spring-beans，spring-context，spring-context-support和spring-expression（SpEL，Spring表达式语言，Spring Expression Language）等模块组成，它们的细节如下：        

- spring-core模块提供了框架的基本组成部分，包括 IoC 和依赖注入功能。
           
- spring-beans 模块提供 BeanFactory，工厂模式的微妙实现，它移除了编码式单例的需要，并且可以把配置和依赖从实际编码逻辑中解耦。
              
- context模块建立在由core和 beans 模块的基础上建立起来的，它以一种类似于JNDI注册的方式访问对象。Context模块继承自Bean模块，并且添加了国际化（比如，使用资源束）、事件传播、资源加载和透明地创建上下文（比如，通过Servelet容器）等功能。Context模块也支持Java EE的功能，比如EJB、JMX和远程调用等。ApplicationContext接口是Context模块的焦点。spring-context-support提供了对第三方库集成到Spring上下文的支持，比如缓存（EhCache, Guava, JCache）、邮件（JavaMail）、调度（CommonJ, Quartz）、模板引擎（FreeMarker, JasperReports, Velocity）等。
                    
- spring-expression模块提供了强大的表达式语言，用于在运行时查询和操作对象图。它是JSP2.1规范中定义的统一表达式语言的扩展，支持set和get属性值、属性赋值、方法调用、访问数组集合及索引的内容、逻辑算术运算、命名变量、通过名字从Spring IoC容器检索对象，还支持列表的投影、选择以及聚合等。

依赖关系如下图：     

![](../pict/1540290875453691.png)
           
### 数据访问/集成
数据访问/集成层包括 JDBC，ORM，OXM，JMS 和事务处理模块，它们的细节如下：
                  
（注：JDBC=Java Data Base Connectivity，ORM=Object Relational Mapping，OXM=Object XML Mapping，JMS=Java Message Service）
               
- JDBC 模块提供了JDBC抽象层，它消除了冗长的JDBC编码和对数据库供应商特定错误代码的解析。
              
- ORM 模块提供了对流行的对象关系映射API的集成，包括JPA、JDO和Hibernate等。通过此模块可以让这些ORM框架和spring的其它功能整合，比如前面提及的事务管理。
           
- OXM 模块提供了对OXM实现的支持，比如JAXB、Castor、XML Beans、JiBX、XStream等。
              
- JMS 模块包含生产（produce）和消费（consume）消息的功能。从Spring 4.1开始，集成了spring-messaging模块。。
               
- 事务模块为实现特殊接口类及所有的 POJO 支持编程式和声明式事务管理。（注：编程式事务需要自己写beginTransaction()、commit()、rollback()等事务管理方法，声明式事务是通过注解或配置由spring自动处理，编程式事务粒度更细）
            
### Web
Web 层由 Web，Web-MVC，Web-Socket 和 Web-Portlet 组成，它们的细节如下：
           
- Web 模块提供面向web的基本功能和面向web的应用上下文，比如多部分（multipart）文件上传功能、使用Servlet监听器初始化IoC容器等。它还包括HTTP客户端以及Spring远程调用中与web相关的部分。。
           
- Web-MVC 模块为web应用提供了模型视图控制（MVC）和REST Web服务的实现。Spring的MVC框架可以使领域模型代码和web表单完全地分离，且可以与Spring框架的其它所有功能进行集成。
              
- Web-Socket 模块为 WebSocket-based 提供了支持，而且在 web 应用程序中提供了客户端和服务器端之间通信的两种方式。
           
- Web-Portlet 模块提供了用于Portlet环境的MVC实现，并反映了spring-webmvc模块的功能。

### 其他
还有其他一些重要的模块，像 AOP，Aspects，Instrumentation，Web 和测试模块，它们的细节如下：
              
- AOP 模块提供了面向切面的编程实现，允许你定义方法拦截器和切入点对代码进行干净地解耦，从而使实现功能的代码彻底的解耦出来。使用源码级的元数据，可以用类似于.Net属性的方式合并行为信息到代码中。
               
- Aspects 模块提供了与 AspectJ 的集成，这是一个功能强大且成熟的面向切面编程（AOP）框架。
           
- Instrumentation 模块在一定的应用服务器中提供了类 instrumentation 的支持和类加载器的实现。
            
- Messaging 模块为 STOMP 提供了支持作为在应用程序中 WebSocket 子协议的使用。它也支持一个注解编程模型，它是为了选路和处理来自 WebSocket 客户端的 STOMP 信息。
           
- 测试模块支持对具有 JUnit 或 TestNG 框架的 Spring 组件的测试。
               
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