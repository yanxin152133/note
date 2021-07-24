# 1. 状态
## 1.1. status
git status命令用于显示工作目录和暂存区的状态。使用此命令能看到那些修改被暂存到了, 哪些没有, 哪些文件没有被Git tracked到。
```bash
git status
```

## 1.2. checkout
git checkout命令用于切换分支或恢复工作树文件。git checkout是git最常用的命令之一，同时也是一个很危险的命令，因为这条命令会重写工作区。

```bash
$ cat test.txt    // 添加一行新内容test1
test
test1


$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   test.txt

no changes added to commit (use "git add" and/or "git commit -a")


$ git checkout -- test.txt    // 把test文件在工作区的修改撤销到最近一次git add 或 git commit时的内容


$ cat test.txt
test

```

## 1.3. reset
git reset命令用于将当前HEAD复位到指定状态。一般用于撤消之前的一些操作(如：git add,git commit等)。

### 1.3.1. git reset HEAD filename
```bash

$ cat test.txt   // 添加一行新内容test1
test
test1


$ git add .


$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   test.txt



$ git reset HEAD test.txt      // 把暂存区的修改撤销掉，重新放回工作区：
Unstaged changes after reset:
M       test.txt


$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   test.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

### 1.3.2. git reset --hard 
```bash
yxc@MacBook-Pro test % cat test.txt 
test
test1
yxc@MacBook-Pro test % vi test.txt 
yxc@MacBook-Pro test % git add .
yxc@MacBook-Pro test % git commit -m "test2"
[master 60c00bf] test2
 1 file changed, 1 insertion(+)
yxc@MacBook-Pro test % git log
commit 60c00bfba7fad0d4d510507be167082f0ebbc621 (HEAD -> master)
Author: yanxin152133 <yanxin152133@gmail.com>
Date:   Sat Jul 24 23:30:01 2021 +0800

    test2

commit b8d6d4dc30d72cf8a783c2a86caaa07e1e693f21
Author: yanxin152133 <yanxin152133@gmail.com>
Date:   Sat Jul 24 23:20:35 2021 +0800

    test.txt
yxc@MacBook-Pro test % git reset --hard HEAD~   // 回退上一个版本   HEAD为当前版本
HEAD 现在位于 b8d6d4d test.txt
yxc@MacBook-Pro test % cat test.txt 
test
test1
```