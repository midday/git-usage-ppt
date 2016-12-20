title: (1)Git 本地操作
speaker: 刘正午
url: https://github.com/midday/git-usage-ppt
transition: slide3
files: /js/zoom.js
theme: moon
usemathjax: yes


[slide]
# Git 本地操作
#### <small><a href="https://github.com/midday/">@刘正午</a></small>
---
## <a class="btn btn-lg btn-success" style="font-size:20px;" href="https://github.com/midday/git-usage-ppt">Download PPT</a>


[slide]
## 目录
---
- Git 简介
- Git 安装与简单配置
- Git 工作流程
- 理解 Git 暂存区
- Git 本地分支与合并
- 查看与对比历史记录
- 撤销修改
- 重写历史记录


[slide]
## Git 简介
- Git 历史
- Git 与 SVN 的对比
- Git 与 SVN 的特点及适用场景
- 为什么要学会使用 Git


[slide]
[magic data-transition="cover-circle"]
## 
----
![](/images/gay.jpg)
====
## Git is Not Gay!!!
====
## Git 作者 Linus
![](/images/git-author.jpg)
[/magic]


[slide]
## Git 历史
<div style="font-size:18px;text-align:left">
<p style="text-indent:2em;">
Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？
</p>
<p style="text-indent:2em;">
事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！  
</p>
<p style="text-indent:2em;">
你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。
</p>
<p style="text-indent:2em;">
不过，到了2002年，Linux系统已经发展了十年了，代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。
</p>
<p style="text-indent:2em;">
安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议（这么干的其实也不只他一个），被BitMover公司发现了（监控工作做得不错！），于是BitMover公司怒了，要收回Linux社区的免费使用权。
</p>
<p style="text-indent:2em;">
Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的。实际情况是这样的：
Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！
</p>
<p style="text-indent:2em;">
Git也由此诞生了。
</p>
</div>

[slide]
## 集中式版本控制 VS 分布式版本控制
![](/images/vcs-jizhongshi.png)
![](/images/vcs-fenbushi.png)

[slide]
## SVN 存储机制 VS Git 存储机制
![](/images/store-svn.png)
![](/images/store-git.png)


[slide] 
## Git 与 SVN 的对比
- Git是分布式的SCM，SVN是集中式的
- Git每个历史版本存储完整的文件，SVN存储文件差异
- Git可离线完成大部分操作，SVN则相反
- Git有着更优雅的分支和合并实现
- Git有更强的撤销修改和修改版本历史的能力
- Git速度更快，效率更高


[slide]
## Git 与 SVN 的特点及适用场景
---
- SVN对中文支持好，操作简单，使用没有难度，美工人员，产品人员，测试人员，实施人员都可轻松上手。使用界面统一，功能完善，操作方便。
- Git 对程序源代码进行差异化的版本管理，代码库占极少的空间。易于代码的分支化管理。不支持中文，图形界面支持差，使用难度大。不易推广。
- **SVN更适用于项目管理， Git仅适用于代码管理。**
 一个研发队伍的成员正常包括：需求分析、设计、美工、程序员、测试、实施、运维，每个成员在工作中都有产出物，  包括了文档、设计代码、程序代码，这些都需要按项目集中进行管理的。SVN能清楚的按目录进行分类管理， 使项目组的管理处于有序高效的状态。


[slide]
## Git 简介-**为什么要学会使用 Git**
---
- 装逼 {:&.rollIn}
- 更好的与大神交流
- 提高自己的市场竞争力


[slide]
## Git 安装与简单配置
---
1. Git 安装  
    [https://git-scm.com](https://git-scm.com)
1. Git 自动完成  
    输入 git 命令后按两下`tab`键
1. Git 终极武器
    ```bash
# git 帮助
$ git --help  
# 浏览器自动打开某命令的帮助文档
$ git config --help
    ```
1. Git 基本配置
    ```bash
$ git config --global user.name 你的名字  
$ git config --global user.email 你的邮箱
    ```
1. Git 子命令配置别名
    ```bash
$ git config --global alias.hist = "log --oneline --decorate --graph --all"
    ```

[slide]
## Git 工作流程
- Git 对象的存储类型及分类
- Git 仓库初始化及克隆
- Git 基本流程

[slide]
## Git 工作流程-**Git 对象的存储类型及分类**
![](/images/git-obj.png)


[slide]
##  Git 工作流程-**Git 仓库初始化及克隆**
![](/images/git-repo-type.png)


[slide]
##  Git 工作流程-**Git 基本流程**
![](/images/git-flow.png)


[slide]
[magic data-transition="cover-circle"]
## Git 暂存区-图解
![](/images/git-cached-01.png)
====
## Git 暂存区-图解
![](/images/git-cached-02.png)
====
## Git 暂存区-图解
![](/images/git-cached-03.png)
====
## Git 暂存区-图解
![](/images/git-cached-04.png)
[/magic]


[slide]
## Git 本地分支与合并
---
1. git branch
2. git tag
3. git checkout(切换分支)
4. git merge


[slide]
## Git 本地分支与合并-**git branch**
- 轻量级标签
```bash
$ git branch test
```
- 删除分支
```bash
git branch -d test
```
- 查看分支信息
```bash
$ git show test
```


[slide]
## Git 本地分支与合并-**git tag**
- 轻量级标签
```bash
$ git tag v0.1.2-light
```
- 附注标签
```bash
$ git tag -a v0.1.2 -m "0.1.2版本"
```
- 删除标签
```bash
git tag -d v0.1.2 
```
- 查看标签信息
```bash
$ git show v0.1.2
```

[slide]
## Git 本地分支与合并-**git tag**


[slide]
## Git 本地分支与合并-**brand、tag图解**
![](/images/git-tag.png)

[slide]
## Git 本地分支与合并-**git checkout**
- *当不指定文件名*，而是给出一个（本地）分支时，那么HEAD标识会移动到那个分支（也就是说，我们“切换”到那个分支了）  
![](/images/git-checkout-02.jpg)


[slide]
## Git 本地分支与合并-**git checkout**
- git checkout -b name来创建并切换到新分支
![](/images/git-checkout-03.jpg)

[slide]
## Git 本地分支与合并-**git merge**
- merge 命令把不同分支合并起来。合并前，索引必须和当前提交相同。如果另一个分支是当前提交的祖父节点，那么合并命令将什么也不做。 另一种情况是如果当前提交是另一个分支的祖父节点，就导致fast-forward合并。指向只是简单的移动，并生成一个新的提交
![](/images/git-merge-01.jpg)


[slide]
## Git 本地分支与合并-**git merge**
- 否则就是一次真正的合并。默认把当前提交(ed489 如下所示)和另一个提交(33104)以及他们的共同祖父节点(b325c)进行一次三方合并。结果是先保存当前目录和索引，然后和父节点33104一起做一次新提交。
![](/images/git-merge-02.jpg)


[slide]
## Git 查看与对比历史记录
---
1. git show
1. git log
1. git diff


[slide]
## Git 查看与对比历史记录-**git show**
- 查看信息


[slide]
## git log
- 查看日志

[slide]
## Git 查看与对比历史记录-**git diff**
![](/images/git-diff.jpg)


[slide]
## Git 撤销修改
---
1. git checkout
1. git reset
1. git clean
1. git revert


[slide]
## Git 撤销修改-**git checkout**
- checkout命令用于从历史提交（或者暂存区域）中拷贝文件到工作目录，也可用于切换分支。


[slide]
## Git 撤销修改-**git checkout**
- *当给定某个文件名*时，git会从指定的提交中拷贝文件到暂存区域和工作目录。比如，git checkout HEAD~ foo.c会将提交节点HEAD~(即当前提交节点的父节点)中的foo.c复制到工作目录并且加到暂存区域中。（如果命令中没有指定提交节点，则会从暂存区域中拷贝内容。）
![](/images/git-checkout-01.jpg)


[slide]
## Git 撤销修改-**git reset**
- reset命令把当前分支指向另一个位置，并且有选择的变动工作目录和索引。也用来在从历史仓库中复制文件到索引，而不动工作目录。
- 如果不给选项，那么当前分支指向到那个提交。
- 如果用--hard选项，那么工作目录也更新
- 如果用--soft选项，那么都不变。
![](/images/git-reset-01.jpg)


[slide]
## Git 撤销修改-**git reset**
- 如果没有给出提交点的版本号，那么默认用HEAD。
- git reset索引回滚到最后一次提交。
- git reset --hard索引和工作区全都回滚到最后一次提交。
![](/images/git-reset-02.jpg)


[slide]
## Git 撤销修改-**git reset**
- 如果给了文件名，那么工作效果和带文件名的checkout差不多，除了索引被更新。
![](/images/git-reset-03.jpg)


[slide]
## Git 撤销修改-**git clean**
- 用来从你的工作目录中删除所有没有tracked过的文件

[slide]
## Git 撤销修改-**git revert**
- 撤销 某次操作，此次操作之前和之后的commit都会被保留，并且 会把这次 撤销 作为一次最新的提交；
- 基本命令
```bash
# 撤销前一次 commit
$ git rever HEAD
#撤销前前一次commit
$git revert HEAD^ 
#比如：fa042ce57ebbe5bb9c8db709f719cec2c58ee7ff）撤销指定的版本，撤销也会作为一次提交进行保存。
$git revert commit
```
![](/images/git-revert-01.png)


[slide]
## 重写历史记录
1. git commit --amend
2. git rebase
3. git reset & git reflog


[slide]
## 重写历史记录-git commit --amend
- 更改一次提交，git会使用与当前提交相同的父节点进行一次新提交，旧的提交会被取消
![](/images/git-commit-amend.jpg)


[slide]
## 重写历史记录-**git rebase**
- 衍合是合并命令的另一种选择。合并把两个父分支合并进行一次提交，提交历史不是线性的。衍合在当前分支上重演另一个分支的历史，提交历史是线性的。
![](/images/git-rebase-01.jpg)


[slide]
## 重写历史记录-**git reflog**
- git reflog常与git reset搭配使用
- HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
- 穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。


[slide]
## 本节完！
