# Linux

可以试着输入git，看看系统有没有安装Git，**如果没安装，将提示如何安装**。

如果你碰巧用Debian或Ubuntu Linux，通过一条`sudo apt-get install git`就可以直接完成Git的安装，非常简单。

老一点的Debian或Ubuntu Linux，要把命令改为`sudo apt-get install git-core`，因为以前有个软件也叫GIT（GNU Interactive Tools），结果Git就只能叫`git-core`了。由于Git名气实在太大，后来就把GNU Interactive Tools改成`gnuit`，`git-core`正式改为`git`。

如果是其他Linux版本，可以直接通过源码安装。先从Git官网下载源码，然后解压，依次输入：`./config`，`make`，`sudo make install`这几个命令安装就好了。



# Windows

从[Git官网](https://git-scm.com/downloads)直接下载安装程序，然后按默认选项安装即可。安装完成后，在开始菜单里找到**“Git”->“Git Bash”**

安装完成后，还需要最后一步设置，在命令行输入：

```Git
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

注意`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

使用`git config user.name`查看设置的用户名