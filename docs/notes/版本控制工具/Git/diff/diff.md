# 1. diff
```bash
$ git diff   // 比较的是工作目录中当前文件和暂存区域快照之间的差异,也就是修改之后还没有暂存起来的变化内容。
diff --git a/test.txt b/test.txt
index 9daeafb..259b241 100644
--- a/test.txt
+++ b/test.txt
@@ -1 +1,2 @@
 test
+test1


$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   test.txt

no changes added to commit (use "git add" and/or "git commit -a")


$ git add .


$ git diff

$ git diff --cached     // 索引区比较
diff --git a/test.txt b/test.txt
index 9daeafb..259b241 100644
--- a/test.txt
+++ b/test.txt
@@ -1 +1,2 @@
 test
+test1

```