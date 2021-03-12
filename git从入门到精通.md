# git从入门到精通

## 关联离线项目到github

```
unzip <repo>.zip   //解压下载下来的zip文件
cd <repo>        //进入到解压后的文件夹路径
git init		//在目录中创建新的git仓库
git add .     //把工作时所有变化提交到暂存区
git remote add origin https://github.com/<user>/<repo>.git  //添加远程仓库
git remote update
git checkout master   //切换到新分支master
```

## 如何上传到GitHub的main分支而不是master分支

```
git push -u origin main  //main即分支名
```

## git下载指定分支代码到本地

```
git clone -b 分支名 网址.git
git clone -b lesson-2 https://github.com/xxx/xxx.git
```

## git回退本地代码

```git
git log -pretty=oneline -2 //查看已提交的版本
/*回退一个版本，且会将暂存区的内容和本地已提交的内容全部恢复到未暂存的状态，不影响原来本地文件(未提交的也不受影响)*/
git reset 版本id  等同于  git reset --mixed '版本id'
/*回退一个版本，不清空暂存区，将已提交的内容恢复到暂存区，不影响原来本地的文件(未提交的也不受影响)*/
git reset --soft '版本id'
/*回退一个版本，清空暂存区，将已提交的内容的版本恢复到本地，本地的文件也将被回复的版本替换*/
git reset --hard '版本id'
```

## 回退远程分支

由于本地分支回滚后，版本将落后远程分支，此时如果用(git push)会报错，必须使用强制推送(git push -f) 覆盖远程分支，否则后面将无法推送到远程分支

```git
git push -f origin '分支名字'
```

git reset 会把回退到的某一版本之前的提交全部撤销，比如三个版本一次提交A1-A2-A3,如果用git reset 回退到A1，那么A2，A3都没了，假如我们只想把A2撤销，并保留着A3，那么就需要使用git revert

```git
git revert -n '版本id'
```

然后一次git add,git commit -m '信息',git push 提交即可