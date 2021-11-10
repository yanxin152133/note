# 1. centos设置http代理
1. 打开配置文件

```html
vi /etc/profile
```
1. 添加

```html
export http_proxy="http://192.168.4.2:10809"
export https_proxy=$http_proxy
export ftp_proxy=$http_proxy
```
1. 执行生效

```html
source /etc/profile
```
1. 查看ip变化

```html
curl ifconfig.io
```