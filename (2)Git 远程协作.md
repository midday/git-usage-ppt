title: (2)Git 远程协作
speaker: 刘正午
url: https://github.com/midday/git-usage-ppt
transition: slide3
files: /js/zoom.js
theme: moon
usemathjax: yes


[slide]
# Git 远程协作
#### <small><a href="https://github.com/midday/">@刘正午</a></small>
---
## <a class="btn btn-lg btn-success" style="font-size:20px;" href="https://github.com/midday/git-usage-ppt">Download PPT</a>


[slide]
## 目录
---
- GitHub 简介
- Git 远程协作的主要命令
- GitHub Pull Request流程

[slide]
## GitHub 简介
---
- GitHub注册与功能简单介绍
- 为GitHub托管项目的访问添加SSH keys
    - window下配置SSH连接GitHub、GitHub配置ssh key
        [http://jingyan.baidu.com/article/a65957f4e91ccf24e77f9b11.html](http://jingyan.baidu.com/article/a65957f4e91ccf24e77f9b11.html)
    - TortoiseGit中SSH密钥的配置方法
        [http://jingyan.baidu.com/article/495ba841f2892638b30edefa.html](http://jingyan.baidu.com/article/495ba841f2892638b30edefa.html)


[slide]
## Git 远程协作的主要命令
---
- git clone
- git fetch
- git pull
- git push


[slide]
## GitHub Pull Request流程
---
- GitHub 上fork项目
- git remote
- Pull Request

[slide]
## 如何保证与上游的代码同步
1. 在 Fork 的代码库中添加上游代码库的 remote 源，该操作只需操作一次即可。
如: 其中# upstream 表示上游代码库名， 可以任意。 
```bash
$ git remote add upstream https://github.scm.corp.ebay.com/montage/frontend-ui-workspace
```
2. 将本地的修改提交 commit
3. 在每次 Pull Request 前做如下操作，即可实现和上游版本库的同步。
```bash
$ git remote update upstream
$ git rebase upstream/{branch name}
```
4. Push 代码到 Github

[slide]
## 本节完！
