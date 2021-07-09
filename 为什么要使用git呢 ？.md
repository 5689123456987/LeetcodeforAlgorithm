![这是你了解的Git吗？](https://pic4.zhimg.com/v2-1a15cfdc8b27a007e4c3d357a05cc1f8_r.jpg)

Git is a [free and open source](http://link.zhihu.com/?target=https%3A//git-scm.com/about/free-and-open-source) distributed version control system designed to handle everything from small to very large projects with speed and efficiency.正如所说的:Git是一个免费开源的分布式版本控制系统，旨在快速并且高效大的为从大到小的项目那个提供版本管理。而针对于公司的开发来说：**为什么要使用git呢 ？**因为 Git 很火，现在很多 IDE 都集成了 Git,并且提供一些相关的图形化操作。也有很多很优秀,专门用来简化 Git 操作的 Git GUI 工具，例如 SourceTree,Tortoise 等。同时分析一下一些常见的版本控制系统。![img](https://pic3.zhimg.com/80/v2-b74c344492c4f89b652761c37bb386be_720w.jpg)

例如SVN与Git的异同点：svn作为集中式的版本控制系统，SVN采用客户端/服务器体系，项目的各种版本都存储在服务器上因此具有以下的特点：
每个版本库有唯一的URL（官方地址），每个用户都从这个地址获取代码和数据；获取代码的更新，也只能连接到这个唯一的版本库，同步以取得最新数据提交必须有网络链接（无本地库）权限控制![img](https://pic4.zhimg.com/80/v2-c88617402db0acc0e746e2e078145563_720w.jpg)

SVN集中式版本控制
缺点：当中央服务器出现单点故障的时候，无法协同工作，同时备份不及时，容易丢失数据。
而Git是一个分布式的管理系统，在本地一个项目都包含一个完整的Git仓库，而且本地仓库和远程仓库通过四种主要传输协议相关联。
因此具有下面的特点：
提交完全在本地完成，无须别人给你授权。冲突解决以及合并更为方便，每个clone版本库都是平等的Git的集中式工作模式非常灵活。采用文件快照的方式进行操作。![img](https://pic2.zhimg.com/80/v2-f6ef43cbfe4d95b362c20bc6800199e1_720w.jpg )

Git工作模式**Git的一些基本操作（1）**
在进行Git的命令了解之前，我们先来看一下Git的工作原理，以及如何完成版本控制。
![img](https://pic3.zhimg.com/80/v2-888920a297fb37a1aa02d75923bf7486_720w.jpg)
工作区：针对于每个开发人员来说，这里就是程序开发，代码编辑的地方暂存区：储存在.git文件夹之中，是本地的临时存储，类似于模拟计算机的组成，内存部分。本地库：是历史版本控制的地方，可以进行版本的控制，提交等等。
针对于本地库的操作：![img](https://pic2.zhimg.com/80/v2-7bb152c9135795f15854278c496b06fd_720w.jpg)

针对于设置签名可以设置仓库的两种级别仓库级别：仅本地库起作用![img](https://pic3.zhimg.com/80/v2-4caea135ffabf4bf0f56222b569e84f2_720w.jpg)![img](https://pic2.zhimg.com/80/v2-acb2d79457e1ce9a2ef4c8c43a771031_720w.jpg)

系统级别：全局



下面我们再尝试一下，创建一个txt并提交到本地仓库：![img](https://pic1.zhimg.com/80/v2-1d2d6ddfe2ea2580cc6a6147bb521630_720w.jpg)

查看本地文件的状态信息

![img](https://pic3.zhimg.com/80/v2-0dd784e8e02f856f976721bf33afc2ca_720w.jpg)

此时文件仍在工作区当中，因此我们需要将它add到暂存区当中![img](https://pic2.zhimg.com/80/v2-71bfcdf1e0bb45e32e1ffdbe4d0ba2d9_720w.jpg)

此时仍可以进行撤回，拉回工作区：![img](https://pic4.zhimg.com/80/v2-67d467c80c207f16d029289eba59ebff_720w.jpg)![img](https://pic4.zhimg.com/80/v2-aa702cf31381b20d4345a03a4deb2aab_720w.jpg)

进行代码的提交以及版本的控制：
![img](https://pic1.zhimg.com/80/v2-4de4322c64ebb07e5059c25f48f2612c_720w.jpg)

这就是对于Git的简单的使用，为的是更加彻底的了解Git的相关操作。









## Git常见问题解决

#### 分支管理

针对于分支的合并来说：

首先可以加入仓库中存在分支A和分支B

需要进行下面的操作：

当分支完成要求之后：

```git
git checkout dev
git pull
git checkout master
git merge dev
git push -u origin master
```

针对于提交时出现下面的问题：

hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

![1625835478839](C:\Users\1\AppData\Local\Temp\1625835478839.png)



主要的问题便是：

1、出现这个错误的原因是git本地仓库的当前版本低于远程仓库的版本(大白话就是：你在github上进行的修改没有同步到本地git仓库中)。 



正确的做法便是：

```
git pull origin main
```

出现下面的问题的时候就需要进行下面的操作：

![1625835653314](C:\Users\1\AppData\Local\Temp\1625835653314.png)

上网查到原因是两个分支是两个不同的版本，具有不同的提交历史 

```
git pull origin master --allow-unrelated-histories
```

可以允许不相关历史提，强制合并，确实解决了这个问题，感谢网友

然后进行上述的合并操作。