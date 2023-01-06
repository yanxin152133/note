# 1. webdav

链接：[hacdias/webdav](https://github.com/hacdias/webdav)

## 1.1. docker 搭建 webdav
运行命令：    

```bash
docker run -it -d --name webdav -v /home/data:/data -v /home/webdav/config:/config -p 8081:8081 --restart unless-stopped hacdias/webdav:latest --config /config/config.yaml
```

配置文件`config.yaml`:
    
```yaml
# 监听任意网卡，多网卡可指定对应ip
address: 0.0.0.0
port: 8081
# 如果无需验证填 false
auth: true
# 如果不需要 https 则填 false
tls: false
# https证书和密钥，如果 tls 为 false，cert 和 key 不需要
#cert: /data/www/cert/szhome.xf1024.com_nginx/cert.pem
#key: /data/www/cert/szhome.xf1024.com_nginx/cert.key
# 访问前缀，建议默认
prefix: /

# 如果 auth 为 false 生效，文件共享的路径
scope: .
# 是否允许修改
modify: true
rules: []

# 跨域设置
cors:
  enabled: true
  credentials: true
  allowed_headers:
    - Depth
  allowed_hosts:
    - http://localhost:8081
  allowed_methods:
    - GET
  exposed_headers:
    - Content-Length
    - Content-Range

# 用户信息，如果 auth 为 true 生效
users:
  - username: cyx
    password: yan1+
    scope: /data/cyx
    modify: true
```