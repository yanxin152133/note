# 1. adguardhome
## 1.1. 运行
```html
docker run --name adguardhome --restart=always  -v /home/adguardhome/work:/opt/adguardhome/work -v /home/adguardhome/conf:/opt/adguardhome/conf -p 53:53/tcp -p 53:53/udp -p 3000:3000/tcp -it -d adguard/adguardhome
```

## 1.2. DNS
### 1.2.1. 上游DNS服务器

```html
tls://dns.pub
https://dns.pub/dns-query
tls://dns.alidns.com
https://dns.alidns.com/dns-query
tls://dns.google
https://dns.google/dns-query
tls://dns11.quad9.net
119.29.29.29
180.76.76.76
114.114.114.114
1.1.1.1
208.67.222.222
```

#### 1.2.1.1. Bootstrap DNS 服务器
```html
222.85.85.85
222.88.88.88
114.114.114.114
119.29.29.29
119.28.28.28
223.5.5.5
223.6.6.6
8.8.8.8
8.8.4.4
9.9.9.11
149.112.112.11
```