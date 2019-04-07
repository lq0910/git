* ## 彻底删除/替换git远程仓库
很简单,将某个工程向现在的仓库强制推送即可

```
$ git remote add origin <url> //url是你git仓库地址
$ git push --force --set-upstream origin master

```
