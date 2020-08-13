# 基于Zookeeper搭建Hadoop高可用集群
>系统版本：CentOS Linux release 7.8.2003 (Core)    
      
>JDK版本：jdk 8u261
      
>Zookeeper：3.4.14
         
>
## 规划
![规划](https://camo.githubusercontent.com/9d815ddad1f979ac693a6d96f2e59c0962a72c14/68747470733a2f2f67697465652e636f6d2f68656962616979696e672f426967446174612d4e6f7465732f7261772f6d61737465722f70696374757265732f6861646f6f70e9ab98e58fafe794a8e99b86e7bea4e8a784e588922e706e67)

## JDK安装
- [Linux下 Java JDK 安装](notes/大数据/大数据常用软件安装/基础软件/JDK安装.md)

## 修改hostname
在三台虚拟机上分别`对应地`执行以下命令:
       
```bash
## hadoop001
[root@hadoop001 ~]$ hostnamectl --static set-hostname hadoop001

## hadoop002
[root@hadoop002 ~]$ hostnamectl --static set-hostname hadoop002

## hadoop003
[root@hadoop003 ~]$ hostnamectl --static set-hostname hadoop003

```
          
## 添加节点
在三台虚拟机上`都`执行以下命令：    
      
```bash
[root@hadoop001 hadoop]# vim /etc/hosts
```
          
在该文件后面`添加`以下内容:   
       
```html
192.168.31.132 hadoop001
192.168.31.133 hadoop002
192.168.31.134 hadoop003
```
         
>192.168.31.132 hadoop001         
192.168.31.133 hadoop002           
192.168.31.134 hadoop003           
分别对应三台虚拟机设置的静态ip和hostname
           
## ssh免密登录
执行以下命令：     
          
```bash
[root@hadoop001 hadoop]# ssh localhost              ## 该命令用于生成隐藏目录.ssh
[root@hadoop001 hadoop]# cd ~/.ssh
[root@hadoop001 hadoop]# ssh-keygen -t rsa #遇到提示一路回车就行
[root@hadoop001 hadoop]# ll #会看到 id_rsa id_rsa.pub 两文件前为私钥，后为公钥
[root@hadoop001 hadoop]# cat id_rsa.pub >> authorized_keys #把公钥内容追加到authorized_keys文件中
[root@hadoop001 hadoop]# chmod 600 authorized_keys #修改文件权限，重要不要忽略
```
          
将密钥分发给其他两台虚拟机：      
           
```bash
[root@hadoop001 hadoop]# cd ~/.ssh
[root@hadoop001 hadoop]# scp * hadoop002:~/.ssh
[root@hadoop001 hadoop]# scp * hadoop003:~/.ssh
```
           
### 验证是否可以免密登录
在`hostname为hadoop001`上执行：
           
```bash
[root@hadoop001 hadoop]# ssh hadoop002
[root@hadoop001 hadoop]# ssh hadoop003
```
         
在`hostname为hadoop002`上执行：
           
```bash
[root@hadoop002 hadoop]# ssh hadoop001
[root@hadoop002 hadoop]# ssh hadoop003
```
           
在`hostname为hadoop003`上执行：
           
```bash
[root@hadoop003 hadoop]# ssh hadoop002
[root@hadoop003 hadoop]# ssh hadoop001
```
          
## Zookeeper
### 下载
```bash
[root@hadoop001]# cd /usr 
[root@hadoop001 usr]# wget https://archive.apache.org/dist/zookeeper/zookeeper-3.4.14/zookeeper-3.4.14.tar.gz
```
          
### 解压
```bash
[root@hadoop001 usr]# tar -zxvf zookeeper-3.4.14.tar.gz
[root@hadoop001 usr]# mv zookeeper-3.4.14 /usr/app
```
     
### 环境变量
```
[root@hadoop001 usr]# vim /etc/profile
```
          
在该文件最后添加以下内容：
          
```html
export ZOOKEEPER_HOME=/usr/app/zookeeper-3.4.14
export PATH=$ZOOKEEPER_HOME/bin:$PATH
```
          
### 修改配置
```bash
[root@hadoop001 usr]# cd /usr/app/zookeeper-3.4.14/conf
```
          
修改为以下内容：    
        
```html
tickTime=2000
initLimit=10
syncLimit=5
dataDir=/usr/local/zookeeper-cluster/data/
dataLogDir=/usr/local/zookeeper-cluster/log/
clientPort=2181

# server.1 这个1是服务器的标识，可以是任意有效数字，标识这是第几个服务器节点，这个标识要写到dataDir目录下面myid文件里
# 指名集群间通讯端口和选举端口
server.1=hadoop001:2287:3387
server.2=hadoop002:2287:3387
server.3=hadoop003:2287:3387
```
           
配置参数说明：
    
- tickTime：用于计算的基础时间单元。比如 session 超时：N*tickTime；
- initLimit：用于集群，允许从节点连接并同步到 master 节点的初始化连接时间，以 tickTime 的倍数来表示；
- syncLimit：用于集群， master 主节点与从节点之间发送消息，请求和应答时间长度（心跳机制）；
- dataDir：数据存储位置；
- dataLogDir：日志目录；
- clientPort：用于客户端连接的端口，默认 2181
          
### 标识节点
执行以下命令：        
```bash
# 三台虚拟机都执行
mkdir -vp  /usr/local/zookeeper-cluster/data/


# hadoop001主机
echo "1" > /usr/local/zookeeper-cluster/data/myid
# hadoop002主机
echo "2" > /usr/local/zookeeper-cluster/data/myid
# hadoop003主机
echo "3" > /usr/local/zookeeper-cluster/data/myid
```
           
### 启动zookeeper
启动命令为：    
      
```bash
/usr/app/zookeeper-3.4.14/bin/zkServer.sh start
```
          
### 验证
查看集群各节点状态的命令为：  
```bash
/usr/app/zookeeper-3.4.14/bin/zkServer.sh status
```
           
如下所示：三个节点进程均启动成功，并且 hadoop001 为 leader 节点，hadoop002 和 hadoop003 为 follower 节点。
            
```bash
[root@hadoop001 conf]# /usr/app/zookeeper-3.4.14/bin/zkServer.sh status
ZooKeeper JMX enabled by default
Using config: /usr/app/zookeeper-3.4.14/bin/../conf/zoo.cfg
Mode: leader
```


```bash
[root@hadoop002 data]# /usr/app/zookeeper-3.4.14/bin/zkServer.sh status
ZooKeeper JMX enabled by default
Using config: /usr/app/zookeeper-3.4.14/bin/../conf/zoo.cfg
Mode: follower
```


```bash
[root@hadoop003 data]# /usr/app/zookeeper-3.4.14/bin/zkServer.sh status
ZooKeeper JMX enabled by default
Using config: /usr/app/zookeeper-3.4.14/bin/../conf/zoo.cfg
Mode: follower
```