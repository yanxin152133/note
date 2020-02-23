# Docker 安装
## 卸载旧版本
旧版本的 Docker 称为 docker 或者 docker-engine，使用以下命令卸载旧版本： 
       
```
sudo apt-get remove docker \
               docker-engine \
               docker.io
```
## 安装与验证
从 Ubuntu 14.04 开始，一部分内核模块移到了可选内核模块包 (linux-image-extra-*) ，以减少内核软件包的体积。正常安装的系统应该会包含可选内核模块包，而一些裁剪后的系统可能会将其精简掉。AUFS 内核驱动属于可选内核模块的一部分，作为推荐的 Docker 存储层驱动，一般建议安装可选内核模块包以使用 AUFS。    

如果系统没有安装可选内核模块的话，可以执行下面的命令来安装可选内核模块包：(操作均为普通用户下)     

```
sudo apt-get update


sudo apt-get install \
    linux-image-extra-$(uname -r) \
    linux-image-extra-virtual
```
          
Ubuntu 16.04 + 上的 Docker CE 默认使用 overlay2 存储层驱动,无需手动配置。    

### 使用APT安装
由于 apt 源使用 HTTPS 以确保软件下载过程中不被篡改。因此，我们首先需要添加使用 HTTPS 传输的软件包以及 CA 证书。      
     
```
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```
      
### 更换国内源
#### 如果过去安装过docker，则先删掉
```bash
sudo apt-get remove docker docker-engine docker.io
```
                
#### 安装依赖
```bash
sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common
```
                             
#### 信任Docker的GPG公钥
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
                        
#### 添加软件仓库
```bash
sudo add-apt-repository \
   "deb [arch=amd64] https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
                     
其他详细内容参考以下文章：
                   
- [Docker Community Edition 镜像使用帮助](https://mirror.tuna.tsinghua.edu.cn/help/docker-ce/)
                 
### 安装 Docker CE

```
sudo apt update
sudo apt install docker-ce
```

### 建立 docker 用户组
建立docker组:   
   
```
sudo groupadd docker
```
    
将当前用户加入docker组：    
    
```
sudo usermod -aG docker $USER
```
                     
退出重新登录即生效。
               
### 关于重新登录后该用户无法正常使用docker的问题
#### 重启docker服务
```bash
sudo service docker restart
```
                      
#### 切换当前会话到新group或者重启X会话
```bash
newgrp - docker
```
                       
### 更换国内Docker仓库
创建文件：       
    
```
sudo vim /etc/docker/daemon.json
```
     
加入以下内容：     
      
```
{
  "registry-mirrors": [
    "https://docker.mirrors.ustc.edu.cn"
  ]
}
```
         
然后重启系统。    
     
### 验证
输入以下命令：       
       
```
docker run hello-world
```
             
若输出以下内容则为成功。          
         
```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
ca4f61b1923c: Pull complete
Digest: sha256:be0cd392e45be79ffeffa6b05338b98ebb16c87b255f48e297ec7f98e123905c
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/
```