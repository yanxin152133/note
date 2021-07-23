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