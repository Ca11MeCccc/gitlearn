												# 					菜鸟教程上的Git简明指南

**创建新仓库**

```
git init
会在本地仓库创建于一个.git的文件夹
```

**要记得设置自己的用户名和邮箱。在每次进行commit的时候，这两个是必须的信息**

```
1.全局设置（对所有git工程都有效）
	设置用户名：git config --global user.name  用户名
	设置邮  箱：git config --global user.email 邮箱
	
2.对特定branch（切换到工程目录下执行）
    设置用户名：git config user.name  用户名
	设置邮  箱：git config user.email 邮箱
```

**将远程仓库的代码clone下来**

```
git clone 远程仓库地址

如:
git clone https://github.com/Ca11MeCccc/gitlearn.git
```

**工作流的组成**

```
你的本地仓库由 git 维护的三棵“树”组成。

第一个是你的 工作目录，它持有实际文件；

第二个是 暂存区（Index），它像个缓存区域，临时保存你的改动；(在被隐藏起来的.git文件夹里)

最后是 HEAD，它指向你最后一次提交的结果。
```

**添加与提交**

```
1.对新增的文件进行添加
	git add 文件名
2.如果不想一个一个添加，可以
	git add * (添加所有的文件)
3.上面的add操作，是将文件add(添加)到 <暂存区>，并没有真正的存入本地的工作目录，所以我们需要将暂存区的文件提交到本地工作目录
	git commit -m "描述一下本次提交是什么的"
```

**推送改动**

```
1. 将本地工作目录的文件推送到远程仓库
git push 远程仓库别名 分支名
如：
git push origin(远程仓库通常都叫这个名字) master

如果我们的本地工作目录不是通过clone远程仓库所得到的，是我们自己创建的。那么此时这个本地工作目录是不带有远程仓库地址的，也就无法推送。所以我们可以将本地工作目录，连接到远程服务器。
2.手动将本地工作目录连接到远程服务器
git remote add origin(起什么名字都OK，但是默许的携程origin) <远程仓库地址>
```

**分支**

```
分支是用来将特性开发绝缘开来的。在你创建仓库的时候，master 是“默认的”分支。在其他分支上进行开发，完成后再将它们合并到主分支上。
使用场景:
	现在是10.16号，还没到双11.但是领导要求我们现在就开始着手双11的活动，要开展一些新的活动。那么此时，分支的优点就来了。我们可以切换到一个新的分支上(比如就叫shuang11)，然后在此分支上进行双11活动的代码的开发。等真正的到了双11，我们再将shuang11这个分支上的代码，合并(merge)到主分支(master)上

1. 创建一个叫做“shuang11”的分支，并切换过去(在哪个分支上创建，那么shuang11的代码就和哪个分支一样。通常是在master上进行创建)
	git checkout -b shuang11(我在这里修改了！用本地的哈)
	
	如果只是创建新分支，则是
	git branch shuang11
2. 切换回主分支
	git checkout master
3. 将指定的分支删除(这里拿shuang11举例)
	git branch -d shuang11
4. 将你想要推送的分支推送到远程服务器
	git push origin <分支名>
```

**如何恢复误删的文件**

```
1. 查看工作区的变化
	git status
2. 知道哪个文件被删除了之后，reset哪个文件
	git reset <文件名，如果有很多，那就是*>
3. 取回被误删的文件
	git cheout <文件名，如果有很多，那就是*>
```

**更新与合并**

```
1. 更新本地仓库至最新改动
	git pull （pull=fetch+merge）
2. 将其他分支合并到当前分支
	(通常是将其他分支合并到master分支)
	git merge <其他分支名>
	如: git merge shuang11

```

**解决冲突**

```
在上面的两种情况下，git 都会尝试去自动合并改动。
	遗憾的是，并非每次都成功，并可能出现冲突（conflicts），即同一行的内容不一样。
		这时候就需要你修改这些文件来手动解决这些冲突（conflicts），可以使用小乌龟。
			改完之后，你需要执行如下命令以将它们标记为合并成功：
			git add <filename>
		在合并改动之前，你可以使用如下命令预览差异：
		git diff <A分支> <B分支> (以A分支为基准，B分支发生的变化)
```



---

# 							廖雪峰的Git教程

Git简介

​	Git的诞生

​	集中式 VS 分布式

安装Git

创建版本库

```
git init 
别用微软自带的记事本对文件进行编辑，打开可以，修改不行
```

```
git add <文件名>
将文件添加到暂存区
```

```
git commit -m "写上本次提交的备注(不可省略)"
将暂存区的文件提交到当前分支
```

时光机穿梭

```
git status
可以查看此刻工作区的状态
```

```
git diff [文件名] [版本A] [版本B]
可以比较版本A和版本B的[文件名]的不同
```

​	版本回退

```
HEAD指向的版本就是当前版本，因此Git可以让我们子版本之间来回穿梭，使用git reset --hard <commitId>

可以用git log来确定此版本之前的版本
可以用git reflog来确定此版本之后的版本
```

​	工作区和暂存区

​		git的本地文件系统就分为3个。一个是工作区working directory，一个暂存区stage(也可以想象成是一个缓冲区的存在)，一个被提交的分支(通常是master)。

​		每次在本地的工作区working directory进行文件的修改之后，我们需要将这些被修改的(或者是新增的)文件添加到暂存区stage，然后将stage



```
参考文档:
1. https://blog.csdn.net/seasermy/article/details/94719709

2. https://www.runoob.com/manual/git-guide/

3. https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424
```

