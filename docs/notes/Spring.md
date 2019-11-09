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
# 程序的耦合及解耦
## 曾经案例中问题
## 工厂模式解耦
# IOC概念和Spring中的IOC
## Spring中基于XML的IOC环境搭建
# 依赖注入（Dependency Injection）