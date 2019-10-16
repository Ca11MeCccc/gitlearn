**创建新仓库**

```
git init

会在本地仓库创建于一个.git的文件夹111
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





```
参考文档:
1. https://blog.csdn.net/seasermy/article/details/94719709

2. https://www.runoob.com/manual/git-guide/
```

