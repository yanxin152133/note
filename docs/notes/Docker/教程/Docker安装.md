# 1. Docker 安装
## 1.1. Centos
### 1.1.1. 卸载旧版本
使用以下命令卸载旧版本：

```html
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```
   
### 1.1.2. Install using the repository
#### 1.1.2.1. Set up the repository
```html
sudo yum install -y yum-utils

sudo yum-config-manager \ 
   --add-repo \
   https://download.docker.com/linux/centos/docker-ce.repo
```

#### 1.1.2.2. Install Docker Engine
```html
sudo yum install docker-ce docker-ce-cli containerd.io
```

如果提示接受GPG密钥，请验证指纹是否与`060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35`匹配。

#### 1.1.2.3. 启动 Docker
```html
sudo systemctl start docker
```

#### 1.1.2.4. 运行 hello-world
```html
sudo docker run hello-world
```

#### 1.1.2.5. 设置开机启动Docker

```html
systemctl enable docker
```

#### 1.1.2.6. centos docker命令补全

```html
# 首先下载 bash-completion
sudo yum install -y bash-completion
# 然后立即生效
source /usr/share/bash-completion/bash_completion
source /usr/share/bash-completion/completions/docker
```
#### 1.1.2.7. 防火墙问题
```html
firewall-cmd --zone=trusted --remove-interface=docker0 --permanent
firewall-cmd --reload
```

## 1.2. Ubuntu
### 1.2.1. 卸载旧版本
使用以下命令卸载旧版本：

```html
sudo apt-get remove docker docker-engine docker.io containerd runc
```

### 1.2.2. Install using the repository
#### 1.2.2.1. Set up the repository
```html
sudo apt-get update

sudo apt-get install \
   apt-transport-https \
   ca-certificates \
   curl \
   gnupg \
   lsb-release
```

#### 1.2.2.2. Add Docker’s official GPG key
```html
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

#### 1.2.2.3. set up the stable repository
X86_64/AMD:

```html
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### 1.2.2.4. Install Docker Engine
```html
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

#### 1.2.2.5. 运行hello-world
```html
sudo docker run hello-world
```

#### 1.2.2.6. 建立 docker 用户组
建立docker组:

```
sudo groupadd docker
```

将当前用户加入docker组：

```
sudo usermod -aG docker $USER
```

退出重新登录即生效。

#### 1.2.2.7. 关于重新登录后该用户无法正常使用docker的问题
##### 1.2.2.7.1. 重启docker服务
```bash
sudo service docker restart
```

##### 1.2.2.7.2. 切换当前会话到新group或者重启X会话
```bash
newgrp - docker
```

## 1.3. 更换国内Docker仓库
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

然后重启Docker。

[Install Docker Engine on CentOS](https://docs.docker.com/engine/install/centos/)     
[Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)     
