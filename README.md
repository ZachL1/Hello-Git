这些内容是在学习廖老师的[Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)时做的笔记，总结在这里。
一方面是为了巩固学习内容；
一方面也方便后续查阅命令；
再就是对有些内容做了适当的更改，比如新版 git 推荐使用 `git switch` 和 `git restore` 替代过时的 `git checkout`......

Git内容很庞大，但学习基础的使用还算比较简单，廖老师的教程写得很好，花一两天时间学下来，提高你效率吧！以后更方便地“同性交友”（狗头 狗头）

---
~~~
下面是各专题的命令大纲，各专题的跳转链接有详细笔记
~~~
[安装git](https://www.wolai.com/heallzy/oSDXSTpmxKjnoV1WAVTVtr)

[创建版本库](https://www.wolai.com/heallzy/3aTGCTEH2jgiJU7J4S6VP)

1. 初始化一个Git仓库，使用`git init`

2. 添加文件到Git仓库，分两步：
使用`git add <file>`，注意，可反复多次使用，添加多个文件；
再使用`git commit -m <message>`

[向仓库提交修改](https://www.wolai.com/heallzy/2o6LdH8K1sfKwFTXazWzvi)

1. 要随时掌握工作区的状态，使用`git status`

2. 如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容

3. 提交修改与提交新文件一样，使用`git add`和`git commit` 

[版本回退](https://www.wolai.com/heallzy/59C7VZuRLgQv2Vj3XztzAJ)

1. `HEAD`指向当前版本，Git允许在不同历史版本之间穿梭，使用命令`git reset --hard commit_id`

2. 穿梭前，用`git log--pretty=oneline--abbrev-commit`查看提交历史，确定要回退到哪个版本及其版本号

3. 要重返未来，用`git reflog`查看历史命令，确定要回到未来的哪个版本

[工作区和暂存区](https://www.wolai.com/heallzy/mvqjB2zhTvG4ZaNmiQ81Kb)

[撤销修改](https://www.wolai.com/heallzy/7LhUqU3eCBiyXLZMYUMCkY)

1. 要丢弃工作区的修改，用`git restore readme.txt`

2. 要丢弃缓存区的修改，用`git restore --staged readme.txt`

3. 要丢弃仓库的修改，用`git reset —- hard HEAD`

[删除文件](https://www.wolai.com/heallzy/3QWdYToQMrCxF9XHtHXV6v)

1. 从库中删除文件：先删除本地，然后`git rm/add`再`git commit`

2. 要恢复文件，使用`git restore`

[使用GitHub](https://www.wolai.com/heallzy/dfjxhesMLMwxD1qpxPcFoM)

1. 准备：在本地创建SSH Key，并将本地SSH公钥添加到GitHub；

2. 要**关联**一个远程库，使用`git remote add <name> git@github.com:19PDP/learngit.git`；

3. 关联后，使用`git push -u <name> master`**第一次推送**master分支的所有内容；

4. 此后，每次本地提交后，使用命令`git push <name> master`即可推送最新修改；

5. 要克隆一个仓库，首先必须知道仓库的地址，然后使用`git clone`命令克隆。

[分支管理](https://www.wolai.com/heallzy/2eo7jUcYZfVD6okPRdTMys)

1. **查看分支**：`git branch`

2. 创建分支：`git branch <name>`

3. 切换分支：`git switch <name>`或者`git checkout <name>`

4. 创建+切换分支：`git switch -c <name>`或者`git checkout -b <name>`

5. **合并某分支**到当前分支：`git merge <name>`

6. **删除分支**：`git branch -d <name>`

7. 当合并分支出现冲突时，git会给出提示，并将文件内容中不同分支中冲突的部分标识出来。
解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。

8. 用`git log --graph`命令可以看到分支合并图。

9. 合并分支时，**加上**`--no-ff`**参数**可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并看不出来曾经做过合并。

[标签管理](https://www.wolai.com/heallzy/9gf33wwPF2wUhNie1DFYC3)

1. 命令`git tag <tagname>`用于新建一个标签，默认为`HEAD`，也可以指定一个commit id；

2. 命令`git tag -a <tagname> -m "blablabla..."`可以指定标签信息；

3. 命令`git tag`可以查看所有标签。

4. 命令`git push origin <tagname>`可以推送一个本地标签；

5. 命令`git push origin --tags`可以推送全部未推送过的本地标签；

6. 命令`git tag -d <tagname>`可以删除一个本地标签；

7. 命令`git push origin :refs/tags/<tagname>`可以删除一个远程标签。
