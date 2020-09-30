# 1. 集群资源管理器YARN
## 1.1. YARN 简介
Apache YARN (Yet Another Resource Negotiator) 是`hadoop 2.0`引入的集群资源管理系统。用户可以将各种服务框架部署在 YARN 上，由 YARN 进行统一地管理和资源分配。
      
![YARN](https://camo.githubusercontent.com/a0309bd39ce152b3dab8f31b55c4a2f3a678136d/68747470733a2f2f67697465652e636f6d2f68656962616979696e672f426967446174612d4e6f7465732f7261772f6d61737465722f70696374757265732f7961726e2d626173652e706e67)
        
## 1.2. YARN架构
![YARN架构](https://camo.githubusercontent.com/0ad1a6f00e3d46cffd4174cc3a235ff948d55dd5/68747470733a2f2f67697465652e636f6d2f68656962616979696e672f426967446174612d4e6f7465732f7261772f6d61737465722f70696374757265732f466967757265334172636869746563747572652d6f662d5941524e2e706e67)
       
### 1.2.1. ResourceManager
`ResourceManager`通常在独立的机器上以后台进程的形式进行，它是整个集群资源的主要协调者和管理者。`ResourceManager`负责给用户提交的所有应用程序分配资源，它根据应用程序优先级、队列容量、ACLs、数据位置等信息，做出决策，然后以共享的、安全的、多租户的方式制定分配策略，调度集群资源。
        
### 1.2.2. NodeManager
`NodeManager`是YARN集群中的每个具体节点的管理者。主要负责该节点内所有容器的生命周期的管理，监视资源和跟踪节点健康。
- 启动时向`ResourceManager`注册并定时发送心跳消息，等待`ResourceManager`的指令；
- 维护`Container`的生命周期，监控`Container`的资源使用情况；
- 管理任务运行时的相关依赖，根据`ApplicationMaster`的需要，在启动`Container`之前将需要的程序及其依赖拷贝到本地。
      
### 1.2.3. ApplicationMaster
在用户提交一个应用程序时，YARN会启动一个轻量级的进程`ApplicationMaster`。`ApplicationMaster`负责协调来自`ResourceManager`的资源，并通过`NodeManager`监视容器内资源的使用情况，同时还负责任务的监控与容错。
- 根据应用的运行状态来决定动态计算资源需求
- 向`ResourceManager`申请资源，监控申请的资源的使用情况
- 跟踪任务状态和进度，报告资源的使用情况和应用的进度信息
- 负责任务的容错
        
### 1.2.4. Container
`Container`是YARN中的资源抽象，它封装了某个节点的多维度资源，如内存、CPU、磁盘、网络等。当AM向RM申请资源时，RM为AM返回的资源是用`Container`表示的。YARN会为每个任务分配一个`Container`，该任务只能使用该`Container`中描述的资源。`ApplicationMaster`可在`Container`内运行任何类型的任务。
      
## 1.3. YARN工作原理简述
当用户向 YARN 中提交一个应用程序后，YARN 将分两个阶段运行该应用程序：第一个阶段是启动 ApplicationMaster；第二个阶段是由 ApplicationMaster 创建应用程序，为它申请资源，并监控它的整个运行过程，直到运行完成，如下图所示:
          
![yarn工作流程](https://live.staticflickr.com/65535/50334526676_e6efbf41c7_z.jpg)
           
上图所示的 YARN 工作流程分为以下几个步骤：

YARN应用工作流程图

1、用户向YARN中提交应用程序，其中包括AM程序、启动AM的命令、命令参数、用户程序等；事实上，需要准确描述运行ApplicationMaster的unix进程的所有信息。提交工作通常由YarnClient来完成。

2、RM为该应用程序分配第一个Container，并与对应的NM通信，要求它在这个Container中启动AM；

3、AM首先向RM注册，这样用户可以直接通过RM査看应用程序的运行状态，运行状态通过 AMRMClientAsync.CallbackHandler的getProgress() 方法来传递给RM。 然后它将为各个任务申请资源，并监控它的运行状态，直到运行结束，即重复步骤4〜7；

4、AM采用轮询的方式通过RPC协议向RM申请和领取资源；资源的协调通过 AMRMClientAsync异步完成,相应的处理方法封装在AMRMClientAsync.CallbackHandler中。

5、—旦AM申请到资源后，便与对应的NM通信，要求它启动任务；通常需要指定一个ContainerLaunchContext，提供Container启动时需要的信息。

6、NM为任务设置好运行环境(包括环境变量、JAR包、二进制程序等)后，将任务启动命令写到一个脚本中，并通过运行该脚本启动任务；

7、各个任务通过某个RPC协议向AM汇报自己的状态和进度，以让AM随时掌握各个任务的运行状态，从而可以在任务失败时重新启动任务；ApplicationMaster与NM的通信通过NMClientAsync object来完成，容器的所有事件通过NMClientAsync.CallbackHandler来处理。例如启动、状态更新、停止等。

8、应用程序运行完成后，AM向RM注销并关闭自己。
          