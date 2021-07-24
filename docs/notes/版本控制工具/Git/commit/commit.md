# 1. commit
git commit命令用于将更改记录(提交)到存储库。将索引的当前内容与描述更改的用户和日志消息一起存储在新的提交中。

## 1.1. 建立文件（本地工作文件夹）
```bash
mkdir test 
cd test
git init
新建index.html文件
```

## 1.2. 追加文件（索引区）
```bash
git status         // 本地工作文件夹状态确认
git add index.html
git status         // 本地工作文件夹状态确认
```

## 1.3. 提交文件（本地库）
```bash
git commit -m "输入提交内容"  // 提交
git log                      // 查看提交历史
```

## 1.4. git commit --amend
>增补提交，会使用与当前提交节点相同的父节点进行一次新的提交，旧的提交将会被取消。

```bash
yxc@MacBook-Pro Github % mkdir test
yxc@MacBook-Pro Github % cd test 
yxc@MacBook-Pro test % git init 
提示：使用 'master' 作为初始分支的名称。这个默认分支名称可能会更改。要在新仓库中
提示：配置使用初始分支名，并消除这条警告，请执行：
提示：
提示：	git config --global init.defaultBranch <名称>
提示：
提示：除了 'master' 之外，通常选定的名字有 'main'、'trunk' 和 'development'。
提示：可以通过以下命令重命名刚创建的分支：
提示：
提示：	git branch -m <name>
已初始化空的 Git 仓库于 /Users/yxc/Github/test/.git/
yxc@MacBook-Pro test % touch test.txt
yxc@MacBook-Pro test % vi test.txt 
yxc@MacBook-Pro test % cat test.txt 
test
yxc@MacBook-Pro test % git add test.txt 
yxc@MacBook-Pro test % git commit -m "test.txt"
[master（根提交） dbb4221] test.txt
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
yxc@MacBook-Pro test % git status
位于分支 master
无文件要提交，干净的工作区
yxc@MacBook-Pro test % git log --oneline 
dbb4221 (HEAD -> master) test.txt
yxc@MacBook-Pro test % vi test.txt 
yxc@MacBook-Pro test % cat test.txt 
test
test1
yxc@MacBook-Pro test % git status 
位于分支 master
尚未暂存以备提交的变更：
  （使用 "git add <文件>..." 更新要提交的内容）
  （使用 "git restore <文件>..." 丢弃工作区的改动）
	修改：     test.txt

修改尚未加入提交（使用 "git add" 和/或 "git commit -a"）
yxc@MacBook-Pro test % git add test.txt 
yxc@MacBook-Pro test % git status         
位于分支 master
要提交的变更：
  （使用 "git restore --staged <文件>..." 以取消暂存）
	修改：     test.txt

yxc@MacBook-Pro test % git commit --amend 
[master b8d6d4d] test.txt
 Date: Sat Jul 24 23:20:35 2021 +0800
 1 file changed, 2 insertions(+)
 create mode 100644 test.txt
yxc@MacBook-Pro test % git status
位于分支 master
无文件要提交，干净的工作区
yxc@MacBook-Pro test % git log --oneline
b8d6d4d (HEAD -> master) test.txt
yxc@MacBook-Pro test %    
```