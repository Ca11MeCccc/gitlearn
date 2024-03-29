

```
参考文档:
1. https://blog.csdn.net/seasermy/article/details/94719709

2. https://www.runoob.com/manual/git-guide/

3. https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424

4. https://github.com/Ca11MeCccc/learngit/blob/master/2019-10/lmx-Hexagram.md
```



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

```
git的本地文件系统就分为3个。一个是工作区working directory，一个暂存区stage(也可以想象成是一个缓冲区的存在)，一个被提交的分支(通常是master)。

每次在本地的工作区working directory进行文件的修改之后，我们需要将这些被修改的(或者是新增的)文件添加到暂存区stage，然后将暂存区stage中的修改commit(提交)到分支中(通常是master)。这样的话，暂存区(stage)就被清空了。
```

​	管理修改(git的本质是对文件的修改进行管理)

```
每次修改，如果不用git add到暂存区，那就不会加入到commit中
(也就是说，并非工作区所有的文件都是需要添加到暂存区并提交到分支的。如果你没有将此文件进行add，那么就让他留在自己的本地工作区working directory，其他人也不知道！)
```

​	撤销修改

```
场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，
分两步，
	第一步用命令git reset HEAD <file>，就回到了场景1，	第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库(提交了就惨咯)。
```

​	删除文件

```
rm <文件名> ： 是直接把文件彻底的删除掉了
我们现在有两种选择：
  1. 我们删除了这个文件，也确实要从版本库中删除该文件。我们可以使用git rm <文件名>，然后commit提交到分支，这样一来，版本库(分支)中这个文件也就真的被删除了(想拿回来可以回退版本，然后取出文件啊，然后再粘贴到最新版本，再add，再commit)
  2. 我们删除了这个文件，但是发现误删了，需要取回这个文件。因为版本库里面还有，所有可以很轻松的将被误删的文件回退到最新版本.
  	git checkout -- <文件名>
  git checkout 的作用就是用版本库里面的版本，来替换工作区的版本。无论工作区修改还是删除，都可以一键还原。
  
  /**
   * 注意：从来没有被添加到版本库(分支)里就被删除的文件，    * 是无法恢复的！
   */
   
 git rm 用于删除一个文件。
 如果这个文件已经被提交到了版本库，那么永远不用担心被误删。但是你要想恢复的话，只能恢复到最新版本，即会丢失<最近的一次提交commit>之后<你又修改的内容>
```

远程仓库

​	添加远程仓库

```
实际情况往往是这样，找一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。
```

​	从远程仓库克隆

```
git clone来克隆一个远程仓库到本地
```

分支管理

```
分支就是科幻电影里面的平行宇宙，当你正在电脑前努力学习Git的时候，另一个你正在另一个平行宇宙里努力学习SVN。

如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，结果，你既学会了Git又学会了SVN！

分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。

现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。
```

创建与合并分支

```
在版本回退里，你已经知道，每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。

截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即master分支。

HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，
(master，branch等相当于指向分支的指针，HEAD是指向master，branch指针的)

所以，HEAD指向的就是当前分支。

一开始的时候，master分支是一条线，Git用master指向最新的提交，再用HEAD指向master，就能确定当前分支，以及当前分支的提交点：


每次提交，master分支都会向前移动一步，这样，随着你不断提交，master分支的线也越来越长。

当我们创建新的分支，例如dev时，Git新建了一个指针叫dev，指向master相同的提交，再把HEAD指向dev，就表示当前分支在dev上：

你看，Git创建一个分支很快，因为除了增加一个dev指针，改改HEAD的指向，工作区的文件都没有任何变化！

不过，从现在开始，对工作区的修改和提交就是针对dev分支了，比如新提交一次后，dev指针往前移动一步，而master指针不变：

假如我们在dev上的工作完成了，就可以把dev合并到master上。

Git怎么合并呢？

最简单的方法，就是直接把master指向dev的当前提交，就完成了合并：
```

![](https://static.liaoxuefeng.com/files/attachments/919022412005504/0)



```
所以Git合并分支也很快！就改改指针，工作区内容也不变！

合并完分支后，甚至可以删除dev分支。删除dev分支就是把dev指针给删掉，删掉后，我们就剩下了一条master分支：
```

![](https://static.liaoxuefeng.com/files/attachments/919022479428512/0)

​	

`git checkout`命令加上`-b`参数表示创建并切换，相当于以下两条命令：

```
$ git branch dev
$ git checkout dev
Switched to branch 'dev
```

`git merge`命令用于合并指定分支到当前分支。合并后，再查看`readme.txt`的内容，就可以看到，和`dev`分支的最新提交是完全一样的。

**注意到上面的`Fast-forward`信息，Git告诉我们，这次合并是“快进模式”，也就是直接把`master`指向`dev`的当前提交，所以合并速度非常快。**

​	删除分支

```
$ git branch -d <分支名>
```

```
Git鼓励大量使用分支：

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>或者git switch <name>

创建+切换分支：git checkout -b <name>或者git switch -c <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>
```

分支管理策略

```
分支策略
在实际开发中，我们应该按照几个基本原则进行分支管理：

首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。

所以，团队合作的分支看起来就像这样：
```

![](https://static.liaoxuefeng.com/files/attachments/919023260793600/0)







**需要临时创建一个分支来进行紧急bug的修复，但是目前的工作进度又不能丢**

git stash 

```
并不是你不想提交，而是工作只进行到一半，还没法提交，预计完成还需1天时间。但是，必须在两个小时内修复该bug，怎么办？

幸好，Git还提供了一个stash功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作：

$ git stash
Saved working directory and index state WIP on dev: f52c633 add merge
现在，用git status查看工作区，就是干净的（除非有没有被Git管理的文件），因此可以放心地创建分支来修复bug。
```



在切换分支并进行相应的操作，然后回到master分支，将原来的分支进行合并，且不想让别人看到自己曾经合并过。

用 git merge --no-ff -m "commit的备注" <将要被合并的分支>

​	--no-ff : 表示不快进模式，no fast forward，就不会保留合并的痕迹了

```
git merge --no-ff -m "merged bug fix 101" issue-101
```





当我们修复完成之后，需要切换会先前的进度

```
工作区是干净的，刚才的工作现场存到哪去了？用git stash list命令看看：

$ git stash list
stash@{0}: WIP on dev: f52c633 add merge

工作现场还在，Git把stash内容存在某个地方了，但是需要恢复一下，有两个办法：

一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；

二是用git stash pop，恢复的同时把stash内容也删了：

$ git stash pop
On branch dev
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   hello.py

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

Dropped refs/stash@{0} (5d677e2ee266f39ea296182fb2354265b91b3b2a)
再用git stash list查看，就看不到任何stash内容了：

$ git stash list
你可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash，用命令：

$ git stash apply stash@{0}
```



```
小结
修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场；

在master分支上修复的bug，想要合并到当前dev分支，可以用git cherry-pick <commit>命令，把bug提交的修改“复制”到当前分支，避免重复劳动。
```







---

# git的知识点小结

1. 部分地方使用了自己的github用户名
2. git config --global user.name "Hexagram" git config --global user.email "[1471685806@qq.com](mailto:1471685806@qq.com)"
   - 登记名字和邮箱以使用git
3. git init 初始化
4. git status
5. git diff
   - git diff HEAD -- *file* 查看*file*在工作区和版本库里最新版本的区别
6. git add
7. git commit -m
8. git log
9. git reset --hard HEAD^
   - git reset HEAD *file* 把暂存区的修改退回的工作区
10. git reflog 记录了使用的每一次命令
11. git checkout -- *file* 丢弃工作区的修改
    - 按情况回到**版本库**或者**暂存区**的状态
    - 实质是使用已存文件替换工作区的版本
12. git reset HEAD *file*
13. git rm *file*

> 连接到远程仓库:

1. ssh-keygen -t rsa -C "

   your_email

   "

   - 建立一个本地的ssh公钥和私钥，再把公钥丢到GitHub上
   - 建立时没有设置密码

2. git remote add origin

    

   git@github.com

   :lmx-Hexagram/ackonwledge_arrangement.git

   - [git@github.com](mailto:git@github.com):用户名/仓库名.git

3. git push -u origin master

   - 第一次使用时需要用-u参数，使其在推送本地master分支的同时，把远程仓库和本地仓库联系起来，以简化以后的命令
   - git push origin master以后只要这样就可以了

4. git clone

    

   git@github.com

   :lmx-Hexagram/ackonwledge_arrangement.git

   - 从远程仓库克隆
   - [git@github.com](mailto:git@github.com):用户名/仓库名.git
   - 也可以使用 git clone https://github.com/lmx-Hexagram/ackonwledge_arrangement.git
   - 也就是可以使用SSH和https两种协议

> 分支:

1. git checkout -b dev

   - Switched to a new branch 'dev'
   - 创建并切换到分支'dev'
   - -b 参数表示创建并切换
   - 以上语句等价于 git branch dev + git checkout dev

2. git branch 列出所有分支

3. git checkout *branch_name*

4. git merge dev

   - 把dev分支的结果合并到'当前所在'分支上
   - 此时是使用`Fast-forward`也就是'快进模式',是直接把master指向dev的当前提交

5. git branch -d dev 删除分支

   - git branch **-D** dev 强制删除没有合并过的分支

6. git switch -c dev 创建并切换的新分支dev

   - git switch *branch_name* 切换到已有的分支
   - **推荐使用switch命令来切换和新建分支**

7. git log --graph 查看分支合并图

8. git merge --no--ff -m "

   say_sth

   "

    

   branch_name

   - 使用`--no--ff`参数使在合并时禁用Fast-forward模式,并创建一个commit

> 暂存工作现场：

1. git stash 保存现在的工作现场(在当前分支)
2. git stash list
3. git stash apply 恢复暂存的工作现场
   - git stash apply stash@{*num*} 使用这种方式指定要恢复的工作现场
4. git stash drop 删除暂存的工作现场
5. git stash pop 恢复并删除
6. git cherry-pick *name_of_commit* 在当前分支重现指定的提交(用来修bug)

> 远程多人合作:

1. git remote -v 查看远程库的信息
2. git push origin *branch_name* 将本地分支推送到origin
3. git checkout -b *branch_name* orgin/*branch_name* 在本地创建和远程分支对应的分支，名字一致(不要在这里乱皮)
4. git branch --set-upstream *branch_name* origin/*branch_name* 建立本地和远程分支的关联

> 标签:

1. git tag命令簇

   - git tag 查看所有标签

   - git tag

      

     tag_name

      

     commit_name

     - for example:
     - *git tag v1.0 378a2a*
     - 若没有*commit_name*则默认给当前分支加标签

   - git show *tag_name* 列出此tag的详细信息

   - git tag -a

      

     tag_name

      

     -m "sth_to_say"

      

     commit_name

     - 打上标签并给标签加上说明

   - git tag -d *tag_name* 删除标签

2. git push origin

    

   tag_name

    

   将标签推送到远程

   - git push origin --tags 将本地所有的标签推送到远程

3. git push origin :refs/tags/*tag_name* 删除远程标签(目前不太懂原理,最好先删除本地标签)

> 在github上工作

1. git clone

    

   git@github.com

   :lmx-Hexagram/learngit.git

   - 先在github上把项目folk到自己的库里，再从github上自己的库里把项目clone下来
   - 在自己本地修改好后，pull到github上自己的库里
   - 在github的项目中发起pull request

> git的自定义：

1. git config --global color.ui true 显示颜色

2. 忽略特殊文件

   - 在工作区根目录创建`.gitignore`文件
   - 在https://github.com/github/gitignore中找到要用的配置文件
   - git add -f *file_name* 强制添加被忽略的文件
   - git check-ignore -v *file_name* 查看时那一条忽略规则，忽略了该文件
   - 还有`.gitignore要放在版本库里，换言之不能忽略该文件，这样可以方面以后管理`

3. git config --global alias.

   the_name_as_your_convinent

    

   command_of_git

   - 以这种方式定义别名，下次使用时可以直接`git *the_name_as_your_convinent*`
   - --global参数使该命令针对这台电脑所有Git仓库有效
   - *git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"* **神仙用法**

> 以上

​																																	lmx-Hexagram

