# 1. mv
git mv命令用于移动或重命名文件，目录或符号链接。

```bash
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   test.txt



$ git mv test.txt test1.txt    


$ ls
test1.txt


$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    test.txt
        new file:   test1.txt

```

# 2. rm
git rm命令用于从工作区和索引中删除文件。