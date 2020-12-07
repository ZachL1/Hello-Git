## 纲要

- 准备：在本地创建SSH Key，并将本地SSH公钥添加到GitHub；

- 要**关联**一个远程库，使用命令`git remote add <name> git@github.com:19PDP/learngit.git`；

- 关联后，使用命令**`git push -u <name> master`****第一次推送**master分支的所有内容；

- 此后，每次本地提交后，只要有必要，就可以使用命令**`git push <name> master`**推送最新修改；

- 要克隆一个仓库，首先必须知道仓库的地址，然后使用**`git clone`**命令克隆。











## 添加ssh公钥到github

> Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。不同机器之间可以远程推送或克隆。当然一台电脑上也可以克隆多个版本库，只要不在同一目录下。
实际情况往往是这样，找一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。
更简单的方式是——**注册一个GitHub账号，就可以免费获得Git远程仓库。**

由于你的本地Git仓库和GitHub仓库之间的传输是通过SSH加密的，所以，需要一点设置：

第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

```Git
$ ssh-keygen -t rsa -C "[youremail@example.com](mailto:youremail@example.com)"
```

你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。

如果一切顺利的话，可以在用户主目录里找到`.ssh`目录，里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是SSH Key的秘钥对，**`id_rsa`****是私钥**，不能泄露出去，**`id_rsa.pub`****是公钥**，可以放心地告诉任何人。

第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：

然后，点“Add SSH Key”，填上任意Title，在Key文本框里**粘贴****`id_rsa.pub`****文件的内容**。

## 添加到远程库

你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让**这两个仓库进行远程同步**，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作。

**第一步**，在GitHub上创建一个新的仓库；

**第二步**，将本地仓库与之关联：

```Git
$ **git remote add github** git@github.com:19PDP/learngit.git
```

添加后，远程库的名字就是`github`，当然你也可以把它叫成别的名字。（git默认叫origin）

**第三步**，把本地库的所有内容推送到远程库上：

```Git
$ git push **-u** github master
Counting objects: 20, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (15/15), done.
Writing objects: 100% (20/20), 1.64 KiB | 560.00 KiB/s, done.
Total 20 (delta 5), reused 0 (delta 0)
remote: Resolving deltas: 100% (5/5), done.
To github.com:michaelliao/learngit.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'github'.
```

把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支`master`推送到远程。

由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

在此之后，只要本地作了提交（即更改提交到了本地仓库），就可以直接把本地`master`分支的最新修改推送至远程库GitHub：

```Git
$ git push github master
```

> 第一次使用Git的clone或者push命令连接GitHub时，会得到一个警告。这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入yes回车即可。

## 从远程库克隆

使用命令`git clone`克隆一个远程库为本地库，克隆GitHub上的一个[`git@github.com`](mailto:git@github.com)`:xlzy520/picgo-plugin-smms-user.git`项目：

```Git
$ git clone **git@github.com:xlzy520/picgo-plugin-smms-user.git**
Cloning into 'picgo-plugin-smms-user'...
remote: Enumerating objects: 48, done.
remote: Counting objects: 100% (48/48), done.
remote: Compressing objects: 100% (35/35), done.
remote: Total 48 (delta 20), reused 35 (delta 10), pack-reused 0
Receiving objects: 100% (48/48), 9.24 KiB | 1.85 MiB/s, done.
Resolving deltas: 100% (20/20), done.
```

在当前目录下将多出一个子目录`picgo-plugin-smms-user`，该目录下即为从远程库克隆到本地的内容。

## 克隆大佬的项目

访问一个项目主页，比如：[https://github.com/iggredible/Learn-Vim](https://github.com/iggredible/Learn-Vim)。点“Fork”就在自己的账号下克隆了一个Learn-Vim仓库，然后，从自己的账号下clone：

```Git
git clone git@github.com:19PDP/Learn-Vim.git
```

**一定要从自己的账号下clone仓库，这样才能推送修改**。如果从Learn-Vim的作者的仓库地址克隆，因为没有权限，你将不能推送修改。