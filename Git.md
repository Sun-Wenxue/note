创建版本库

```
git init
git add <file>
git commit -m <message>
```

查看状态

```
git status
git diff
git log
```

回退版本

```
git reset --hard HEAD^
```

HEAD^上一个版本

HEAD^^上上一个版本

HEAD~100上100个版本

--hard 回退到上一个版本的已提交状态

--soft回退到上一个版本的未提交状态

--mixed回退到上个版本已添加但未提交的状态

记录命令（回到未来版本）

```
git reflog
```

撤销修改

```
git checkout -- <file>
```

让这个文件回到最近一次git commit或git add时的状态

撤销暂存(撤销add)

```
git reset HEAD <file>
```

删除文件

```
git rm <file>
```

相当于rm+git add

通过SSH链接远程仓库

```
ssh -keygen -t -rsa -C "email@xx.com"
在github添加id_rsa.pub
git remote add origin git@github.com:xx
git push -u origin master
```

远程库信息

```
git remote -v
```

删除远程库（的绑定）

```
git remote rm origin
```

从远程库克隆

```
git clone git@github.com:xx
```

创建和切换分支

```
git branch dev
git checkout dev
```

相当于

```
git checkout -b dev
```

查看当前分支

```
git branch
*dev（当前）
master
```

合并分支

```
git merge dev
```

删除分支

```
git branch -d dev
```

临时储藏工作现场

```
git stash
```

查看

```
git stash list
```

恢复

```
git stash apply 恢复
git stash drop 删除
git stash pop 恢复的同时删除
```

多人协作，在分支开发：在本地创建分支，拉取远程分支，推送分支

变基

```
git rebase
```

提交历史简洁、线性，适合个人分支的整理。

merge会保留分支的分叉历史，适合团队协作

打标签：将当前分支和最近的commit对应的commit id打标签

```
git tag -a <name> (commit id) -m "xx"
```

查看所有标签

```
git tag
```

查看标签信息

```
git show <name>
```

删除标签

```
git tag -d <name>
```

推送标签

```
git push origin <name>/ --tags
```

删除已经推送到远程的标签

```
git tag -d <name>
git push origin :refs/tags/<name>
```

忽略特殊文件

```
.gitignore
```

别名

```
$ git config --global alias.st status
```

