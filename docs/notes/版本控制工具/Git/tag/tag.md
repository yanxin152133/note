# 1. tag
>git tag命令用于创建，列出，删除或验证使用GPG签名的标签对象。

```bash
yxc@MacBook-Pro test % git tag
yxc@MacBook-Pro test % git tag v1.0.0    // 创建标签
yxc@MacBook-Pro test % git tag 
v1.0.0
yxc@MacBook-Pro test % touch test1
yxc@MacBook-Pro test % git add .
yxc@MacBook-Pro test % git commit -m "test1"
[master 788eef3] test1
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1
yxc@MacBook-Pro test % git tag v1.0.1   // 创建标签
yxc@MacBook-Pro test % git tag
v1.0.0
v1.0.1
yxc@MacBook-Pro test % touch test2
yxc@MacBook-Pro test % git add test2 
yxc@MacBook-Pro test % git commit -m "test2"
[master 73bb718] test2
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2
yxc@MacBook-Pro test % git tag v1.0.2   // 创建标签
yxc@MacBook-Pro test % git tag 
v1.0.0
v1.0.1
v1.0.2
yxc@MacBook-Pro test % git tag -l 'v1.0.*'    // 列出v1.0.* 有关的标签
v1.0.0
v1.0.1
v1.0.2
yxc@MacBook-Pro test % git show v1.0.1
commit 788eef337a907a95bdba3bdef4d0b4af274f7fa9 (tag: v1.0.1)
Author: yanxin152133 <yanxin152133@gmail.com>
Date:   Sun Jul 25 00:52:30 2021 +0800

    test1

diff --git a/test1 b/test1
new file mode 100644
index 0000000..e69de29
```

## 1.1. git show
>git show 命令查看相应标签的版本信息，并连同显示打标签时的提交对象

```bash
yxc@MacBook-Pro test % git show v1.0.1
commit 788eef337a907a95bdba3bdef4d0b4af274f7fa9 (tag: v1.0.1)
Author: yanxin152133 <yanxin152133@gmail.com>
Date:   Sun Jul 25 00:52:30 2021 +0800

    test1

diff --git a/test1 b/test1
new file mode 100644
index 0000000..e69de29
```