# 使用Docker搭建TensorFlow环境
## 相关准备工作
1. 更换国内软件源    
这里使用华为云的`sources.list`    
                
```bash

sed -i "s@http://.*archive.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list
sed -i "s@http://.*security.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list
```
           
2. `apt update`       
更换过软件源之后需要输入以下命令：
             
```bash
sudo apt update        ## 在root用户下则省略sudo


## 如果有需要进行更新的则使用以下命令,无则跳过
sudo apt upgrade -y    ## 在root用户下则省略sudo
```
            
3. 安装`tmux` 软件     
tmux 是一款终端复用命令行工具，一般用于 Terminal 的窗口管理。
        
```bash
sudo apt install tmux -y    ## 在root用户下则省略sudo
```
                
## 安装docker
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
      
鉴于国内网络问题，强烈建议使用国内源，官方源请在注释中查看。    
为了确认所下载软件包的合法性，需要添加软件源的 GPG 密钥。     
      
```
(任选其一即可)
curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add -


官方源
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
     
然后，我们需要向 source.list 中添加 Docker 软件源     
      
```
sudo add-apt-repository \
    "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
    $(lsb_release -cs) \
    stable"


# 官方源
# $ sudo add-apt-repository \
#    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
#    $(lsb_release -cs) \
#    stable"
```
      

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
          
### 查看已下载的镜像
```bash
docker images
```
            
示例：          
          
```bash
root@002:~# docker images
REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
yancccccc/mysql5.6-utf8   latest              721bb6b0b741        10 days ago         286MB
yancccccc/php-apache      latest              e6f4473bc17d        4 weeks ago         263MB
```
           
### 查看正在运行的容器
```bash
docker ps -a
```
            
示例：      
        
```bash
root@002:~# docker ps -a
CONTAINER ID        IMAGE                     COMMAND                  CREATED             STATUS              PORTS                    NAMES
ea7b18474ae3        yancccccc/mysql5.6-utf8   "docker-entrypoint.s…"   10 days ago         Up 27 hours         0.0.0.0:3306->3306/tcp   mysql
a1c840339bd8        yancccccc/php-apache      "/bin/bash"              4 weeks ago         Up 27 hours         0.0.0.0:80->80/tcp       php-apache
```
          
上面的示例中运行着两个容器，两个容器的名字分别为php-apache和mysql。
             
### 停止与删除容器
```bash
docker stop xxx      ## xxx 为容器的名字
docker rm XXX       ## xxx为上一步中已停止的容器
```

示例：      

```bash
## 根据上一步查看正在运行的容器一步中的示例
## 停止php-apache这个容器
docker stop php-apache
## 删除上一个命令已停止的php-apache容器
docker rm php-apache
```
       
### 删除镜像
```bash
docker rmi xxx    ## xxx为镜像名字
```

示例：            
           
```bash
## 根据上一步查看正在运行的容器一步中的示例
## 删除php-apache镜像
docker rmi yancccccc/php-apache
```
            
