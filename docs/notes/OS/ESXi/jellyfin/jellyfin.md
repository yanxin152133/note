# 1. jellyfin
## 1.1. 显卡
```html
root@jellyfin:/# ls /dev/dri/
by-path  card0  card1  renderD128  renderD129
```

## 1.2. 运行
```html
docker run -d --name jellyfin --volume /data/jellyfin/config:/config  --volume /data/jellyfin/cache:/cache  --volume /data/resource:/media  --net=host  --restart=always  --device /dev/dri/renderD128:/dev/dri/renderD128  --device /dev/dri/card0:/dev/dri/card0  jellyfin/jellyfin
```

## 1.3. 开启硬解
jellyfin控制台开启硬件加速VAAPI。