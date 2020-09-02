# Linux环境下Hive的安装
>系统版本：CentOS Linux release 7.8.2003 (Core)    
      
>JDK版本：jdk 8u261
      
>Zookeeper：3.4.14
         
>hadoop：hadoop-2.6.0-cdh5.15.2
        
>Hive：cdh5.15.2
         
## 前提
- [Linux下 Java JDK 安装](notes/大数据/大数据常用软件安装/基础软件/JDK安装.md)
- [基于Zookeeper搭建Hadoop高可用集群](notes/大数据/大数据常用软件安装/Hadoop/基于Zookeeper搭建Hadoop高可用集群.md)
       
## 下载
下载地址：http://archive.cloudera.com/cdh5/cdh/5/
       
## 解压
```bash
[root@localhost usr]# tar -zxvf hive-1.1.0-cdh5.15.2.tar.gz -C app/
```
        
## 配置环境变量
```bash
[root@localhost hive-1.1.0-cdh5.15.2]# vim /etc/profile
```
       
将以下内容加入该文件末尾：
       
```html
# hive
export HIVE_HOME=/usr/app/hive-1.1.0-cdh5.15.2
export PATH=$HIVE_HOME/bin:$PATH
```
       
使配置立即生效。
        
```bash
[root@localhost hive-1.1.0-cdh5.15.2]# source /etc/profile
```
        
## 配置
进入`conf`目录，对以下文件进行配置修改。
       
### hive-env.sh
```bash
[root@localhost conf]# cp hive-env.sh.template hive-env.sh
[root@localhost conf]# vim hive-env.sh
```
       
修改为以下内容：
       
```html
HADOOP_HOME=/usr/app/hadoop-2.6.0-cdh5.15.2
```
### hive-site.xml
