Git is a [free and open source](https://git-scm.com/about/free-and-open-source) distributed version control system designed to handle everything from small to very large projects with speed and efficiency. 



正如所说的:

Git是一个免费开源的分布式版本控制系统，旨在快速并且高效大的为从大到小的项目那个提供版本管理。

而针对于公司的开发来说：

## 为什么要使用git呢 ？

因为 Git 很火，现在很多 IDE 都集成了 Git,并且提供一些相关的图形化操作。也有很多很优秀,专门用来简化 Git 操作的 Git GUI 工具，例如 SourceTree,Tortoise 等。 

同时分析一下一些常见的版本控制系统。

例如SVN与Git的异同点：

1. svn作为集中式的版本控制系统，SVN采用客户端/服务器体系，项目的各种版本都存储在服务器上因此具有以下的特点：

   

   - 每个版本库有唯一的URL（官方地址），每个用户都从这个地址获取代码和数据；获取代码的更新，也只能连接到这个唯一的版本库，同步以取得最新数据
   - 提交必须有网络链接（无本地库）
   - 权限控制

   

   

   缺点：当中央服务器出现单点故障的时候，无法协同工作，同时备份不及时，容易丢失数据。

   

2. 而Git是一个分布式的管理系统，在本地一个项目都包含一个完整的Git仓库，而且本地仓库和远程仓库通过四种主要传输协议相关联。

   因此具有下面的特点：

   - 提交完全在本地完成，无须别人给你授权。
   - 冲突解决以及合并更为方便，每个clone版本库都是平等的
   - Git的集中式工作模式非常灵活。
   - 采用文件快照的方式进行操作。

   ## Git的一些基本操作（1）

   在进行Git的命令了解之前，我们先来看一下Git的工作原理，以及如何完成版本控制。

   



