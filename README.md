## 

```bash
git reset —hard HEAD^
git reset HEAD file
git checkout -- file
```
## 1.管理修改
>第一次修改 -> git add -> 第二次修改 -> git add -> git commit

## 2.撤销修改
```bash
git checkout — <file> #这个文件回到最近一次git commit或git add时的状态。

# 取消add操作
git reset HEAD file #可以把暂存区的修改撤销掉（unstage），重新放回工作区
```
## 3.版本回退
```bash
git add <file>
git commit -m “version number”

git reset —hard HEAD^ 回退版本
git reset — hard HEAD^^ #可以用git log 查看过去的提交历史 

git reset — hard <commit_id > # git reflog可以查看命令的历史，确定回到未来的哪个版本

```

#### example:
>场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
>场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
>场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，git reset —hard HEAD^ ，不过前提是没有推送到远程库。

## 4.删除文件
```bash
rm file
git rm file 
git commit -m “remove file”
#删除错误 可以用版本库里的版本替换工作区的版本 git checkout —file
```


## 5.添加到远程仓库
```bash
git remote add origin git@github.com:Clowlar/learngit.git
git push -u origin master
```
## 6.从远程库克隆
```bash
git clone git@github.com:Clowlar/getskills.git
```

## 7.分支管理

>查看分支：git branch

>创建分支：git branch <name>

>切换分支：git checkout <name>

>创建+切换分支：git checkout -b <name>

>合并某分支到当前分支：git merge <name>

>合并分支 (禁用fast forward) git merge --no-ff -m "merge with no-ff" devgit 

>删除分支：git branch -d <name>

## 8.多人协作

#### 推送分支
```bash
git push origin master
```
```bash
git push origin dev
```
#### 抓取分支
```bash
git checkout -b dev origin/dev
```
#### 提交 
```bash
git push origin dev
```

#### 有冲突
```bash
git pull
```

#### 没有指定本地dev分支与远程origin/dev分支的链接
```bash
git branch --set-upstream dev origin/dev
```

####
>因此，多人协作的工作模式通常是这样：
首先，可以试图用git push origin branch-name推送自己的修改；
如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
如果合并有冲突，则解决冲突，并在本地提交；
没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！
如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name。
这就是多人协作的工作模式，一旦熟悉了，就非常简单。

