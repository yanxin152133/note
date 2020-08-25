# 1. Flink集群部署
>系统版本：CentOS Linux release 7.8.2003 (Core)    
      
>JDK版本：jdk 8u261
     
>Zookeeper：3.4.14
         
>hadoop：hadoop-2.6.0-cdh5.15.2
        
>Flink:
## 1.1. 前提
- [Linux下 Java JDK 安装](notes/大数据/大数据常用软件安装/基础软件/JDK安装.md)
- [Zookeeper集群环境搭建](notes/大数据/大数据常用软件安装/zookeeper/Zookeeper集群环境搭建.md)
- [基于Zookeeper搭建Hadoop高可用集群](notes/大数据/大数据常用软件安装/Hadoop/基于Zookeeper搭建Hadoop高可用集群.md)

## 1.2. flink
### 1.2.1. 下载
- [flink](https://flink.apache.org/downloads.html)
       
### 1.2.2. 解压
```bash
[root@hadoop001 usr]# tar -zxvf flink-1.9.1-bin-scala_2.12.tgz -C /usr/app/
```
       
### 1.2.3. 配置环境变量
```bash
[root@hadoop001 usr]# vim /etc/profile
```
       
将以下内容添加到末尾：
       
```html
export FLINK_HOME=/usr/app/flink-1.9.1
export PATH=$FLINK_HOME/bin:$PATH
```
         
### 1.2.4. 添加Hadoop组件包
在官网的下载页面找到以下内容，点击下载。并将下载的文件上传到`/usr/app/flink-1.9.1/lib`路径下。
       
![](https://camo.githubusercontent.com/dc7293eb963224390bc2963ace2a357cfcac8991/68747470733a2f2f67697465652e636f6d2f68656962616979696e672f426967446174612d4e6f7465732f7261772f6d61737465722f70696374757265732f666c696e6b2d6f7074696f6e616c2d636f6d706f6e656e74732e706e67)
         
### 1.2.5. 配置flink
进入到`/usr/app/flink-1.9.1/conf`路径下。对以下文件进行修改
     
#### 1.2.5.1. masters
对`masters`文件进行修改：
      
```html
hadoop001:8081
hadoop002:8081
```
         
#### 1.2.5.2. slaves
对`slaves`文件进行修改：
      
```html
hadoop002
hadoop003
```
       
#### 1.2.5.3. flink-conf.yaml
对``flink-conf.yaml`文件添加以下内容：
      
```html
# 配置使用zookeeper来开启高可用模式
high-availability: zookeeper
# 配置zookeeper的地址，采用zookeeper集群时，可以使用逗号来分隔多个节点地址
high-availability.zookeeper.quorum: hadoop001:2181,hadoop002:2181,hadoop003:2181
# 在zookeeper上存储flink集群元信息的路径
high-availability.zookeeper.path.root: /flink
# 集群id
high-availability.cluster-id: /standalone_cluster_one
# 持久化存储JobManager元数据的地址，zookeeper上存储的只是指向该元数据的指针信息
high-availability.storageDir: hdfs://hadoop001:8020/flink/recovery
```
          
### 1.2.6. 分发安装包
```bash
[root@hadoop001 conf]# scp -r /usr/app/flink-1.9.1/ hadoop002:/usr/app/
[root@hadoop001 conf]# scp -r /usr/app/flink-1.9.1/ hadoop003:/usr/app/
```
        
## 1.3. 启动
1. 启动zookeeper
2. 启动Hadoop
3. 启动flink
      
### 1.3.1. 启动flink
```bash
[root@hadoop001 hadoop]# cd /usr/app/flink-1.9.1/bin/
[root@hadoop001 bin]# ./start-cluster.sh
Starting HA cluster with 2 masters.
Starting standalonesession daemon on host hadoop001.
Starting standalonesession daemon on host hadoop002.
Starting taskexecutor daemon on host hadoop002.
Starting taskexecutor daemon on host hadoop003.
```
         
## 1.4. 验证集群是否启动
### 1.4.1. 相关进程
```bash
[root@hadoop001 conf]# jps
6963 Jps
2996 QuorumPeerMain
5190 StandaloneSessionClusterEntrypoint
3147 NameNode
3467 JournalNode
3260 DataNode
3647 DFSZKFailoverController


[root@hadoop002 sbin]# jps
4832 StandaloneSessionClusterEntrypoint
2706 QuorumPeerMain
2851 DataNode
2932 JournalNode
5285 TaskManagerRunner
3016 DFSZKFailoverController
2782 NameNode
5854 Jps


[root@hadoop003 sbin]# jps
4643 Jps
4344 TaskManagerRunner
2858 JournalNode
2717 QuorumPeerMain
3679 ResourceManager
```


