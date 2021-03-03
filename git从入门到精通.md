# git从入门到精通

#### 关联离线项目到github

```
unzip <repo>.zip   //解压下载下来的zip文件
cd <repo>        //进入到解压后的文件夹路径
git init		//在目录中创建新的git仓库
git add .     //把工作时所有变化提交到暂存区
git remote add origin https://github.com/<user>/<repo>.git  //添加远程仓库
git remote update
git checkout master   //切换到新分支master
```

#### 如何上传到GitHub的main分支而不是master分支

```
git push -u origin main  //main即分支名
```

#### git下载指定分支代码到本地

```
git clone -b 分支名 网址.git
git clone -b lesson-2 https://github.com/xxx/xxx.git
```

