# 基本原理
> Git 管理项目时，文件在三个区域转移：工作区，暂存区，以及本地仓库。

![git1](https://cdn.loggerhead.me/images/git-areas.png)

 简单的说，工作区就是 .git 所在目录，暂存区就是 .git/index 文件，本地仓库就是 .git 目录。实际上，暂存区是一个包含文件索引的目录树，记录了文件的各种信息（文件名、文件长度、修改时间等），而文件内容则存放在 .git/objects 目录下。
 
 ![git2](https://cdn.loggerhead.me/images/git-stage.png)
 
 Git 将 commit、文件、目录统统视为对象。对象以 SHA1 值作为指纹，与其他对象相区分，Git 命令操作的最小单位是对象。 Git 会将文件的副本存放在 .git 文件夹下，每个文件都根据文件内容进行操作。

![git3](https://cdn.loggerhead.me/images/git-commit-and-tree.png)

由 Git 管理的文件始终在四种状态之间迁移，分别是：未跟踪（Untracked）、未修改（Unmodified）、已修改（Modified）或已暂存（Staged）。

![git4](https://cdn.loggerhead.me/images/git-lifecycle.png)

HEAD、分支（branch）、标签（tag）都是指针，均直接或间接指向相应的 commit。HEAD 始终指向当前分支，分支和标签指向对应的 commit。通过 git cat-file -p <SHA1> 可查看 commit 内容。
  
  ```
  $ cat .git/HEAD
  ref: refs/heads/master
  $ cat refs/heads/master
  44181f5600579209649bf30c2dbe9227c68a3a58
  $ cat refs/tags/v0.1
  0d84e16dc2e19a309865202a4d2d2e267c1f315e
  $ git cat-file -p 0d84e16dc2e19a309865202a4d2d2e267c1f315e
  tree 7b2366b4fb6aa745d1ad542be660cab47ca6247e
  parent 0acf7329fb3dec0a4f4eef2ae0d6c0e376435300
  author loggerhead <lloggerhead@gmail.com> 1434017010 +0800
  committer loggerhead <lloggerhead@gmail.com> 1434017010 +0800

  add ldconfig explain
  ```
