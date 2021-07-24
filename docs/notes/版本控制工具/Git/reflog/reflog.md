# 1. reflog
>返回过去之后，通过` git reflog `命令找到现在的位置（commit_id），再从过去返回回来。

```bash
yxc@MacBook-Pro test % git reflog 
b8d6d4d (HEAD -> master) HEAD@{0}: reset: moving to HEAD~
60c00bf HEAD@{1}: reset: moving to 60c00bfba7fad0d4d510507be167082f0ebbc621
b8d6d4d (HEAD -> master) HEAD@{2}: reset: moving to HEAD~
60c00bf HEAD@{3}: commit: test2
b8d6d4d (HEAD -> master) HEAD@{4}: commit (amend): test.txt
dbb4221 HEAD@{5}: commit (initial): test.txt
```