---
title: 解决Hexo在Git上同步问题
date: 2017-04-19 11:50:32
tags:
categories: 随笔
---
## 1. 需要的工具

* node.js
* Git
* Hexo环境

##  2.将主体的工程发送到yourname.github.io工程的分支hexo上

切换到工程文件夹，右击菜单--*git bash here*

```
git init //初始本地仓库
git add .
git commit -m "My blog hexo"
git branch hexo //新建一个hexo分支
git checkout hexo //切换到hexo分支
git remote add origin git@github.com:yourname/yourname.github.io.git  //将本地与Github项目对接
git push origin hexo  //push到Github项目的hexo分支上
```

这样就可以将 hexo工程放到github了



## 3.其他终端

现将工程clone下来

```
git clone -b hexo git@github.com:yourname/yourname.github.io.git 
```

然后在clone下来的文件夹中。右击菜单--*git bash here*

注意：hexo工程已经存在了不需要再进行 init了

直接

```
$ npm install
```

> 如果只是更新了一片博客 只需要将source文件夹提交即可

```
$ git add .
$ git commit -m"更新的内容"
$ git push origin hexo
```



