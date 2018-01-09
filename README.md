## 版本回退
```bash
git add <file>
git commit -m “version number”

git reset —hard HEAD^ 回退版本
git reset — hard HEAD^^ #可以用git log 查看过去的提交历史 
git reset — hard <commit_id > # git reflog可以查看命令的历史，确定回到未来的哪个版本

```

## 管理修改
第一次修改 -> git add -> 第二次修改 -> git add -> git commit

## 撤销修改
```bash
git checkout — <file> #这个文件回到最近一次git commit或git add时的状态。
git reset HEAD file #可以把暂存区的修改撤销掉（unstage），重新放回工作区
```


#### example:
##### 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
##### 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
##### 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，git reset —hard HEAD^ ，不过前提是没有推送到远程库。

## 删除文件
```bash
rm file
git rm file 
git commit -m “remove file”
#删除错误 可以用版本库里的版本替换工作区的版本 git checkout —file
```


##添加到远程仓库
```bash
git remote add origin git@github.com:Clowlar/learngit.git
git push -u origin master
```
##从远程库克隆
```bash

git clone git@github.com:Clowlar/getskills.git
```

