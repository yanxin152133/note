# Linux环境下Hive的安装
>系统版本：CentOS Linux release 7.8.2003 (Core)  
      
>Hive：cdh5.15.2
       
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