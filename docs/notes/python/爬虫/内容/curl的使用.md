# curl的使用
## 简介
curl 是常用的命令行工具，用来请求 Web 服务器。它的名字就是客户端（client）的 URL 工具的意思。
## 安装
```bash
apt install curl
apt install openssl 或  apt install openssl-dev
```
      
## 一些参数的用法
|参数|说明|示例|
|:-:|:-:|:-:|
|-A|指定客户端的用户代理标头|curl -A 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36' https://google.com|
|-b|用来向服务器发送Cookie|curl -b 'foo=bar' https://google.com|
|-c|将服务器设置的Cookie写入一个文件|curl -c cookies.txt https://www.google.com|
|-d|用于发送POST请求的数据体|curl -d'login=emma＆password=123'-X POST https://google.com/login|
|-H|添加HTTP请求的标头|curl -H 'Accept-Language: en-US' https://google.com|
|-i|打印出服务器回应的HTTP标头|curl -i https://www.baidu.com|
|-I|向服务器发出HEAD请求，然后会将服务器返回的HTTP标头打印出来|curl -I https://www.baidu.com|
|-k|指定跳过SSL检测|curl -k https://www.baidu.com|
|-o|将服务器的回应保存成文件|curl -o example.html https://www.baidu.com|
|-O|将服务器回应保存成文件，并将URL的最后部分当作文件名|curl -O https://www.baidu.com/demo.html|
     
## 参考
[curl 的用法指南](https://www.ruanyifeng.com/blog/2019/09/curl-reference.html)