# 1. gitea
```bash
docker run --name=gitea -d --restart=always -p 10022:22 -p 10880:3000 -v /home/ubuntu/gitea:/data -v /home/ubuntu/gitea/config:/data/gitea/conf/ gitea/gitea:latest
```