# GIT 上传文件到远程仓库（github）

###  一 . 本地相关操作

#### 1.1 本地git相关操作

1. 设置当前电脑用户名和邮箱
   * `git config --global user.name "your name(你想要设置的用户名)"` 
   * `git config --global user.email "12@qq.com(你想要设置的邮箱)"` 
2. 初始化本地文件夹
   * `git init`    此命令将将目录变成 **Git** 可以管理的仓库
3. 添加文件到 **git** 本地仓库暂存区
   * `git add fileName(文件、文件夹名)` 
   * `git add .`   添加当前目录下所有文件
4. 提交日志
   * `git commit -m "日志描述"` 
5. 提交文件、代码
   * `git push <远程主机名origin> <远程分支名>` 



#### 1.2 远程gitHub仓库

1. 创建 **SSH Key**  
   * `ssh-Keygen -t rsa -C "12@qq.com(你要设置的邮箱名称)"` <br>**注意：** 命令行区分大小写，上面命令中的 **"C"** 为大写。
   * 设置完成后你可以在提示的相关目录下找 **.shh** 文件夹，里面有 **id_rsa（私钥）** 和 **id_rsa.pub（公钥）** 两个文件，公钥可以放心的告诉别人。
2. 登陆 **GitHub** ==>  **settings**    ==>    **SSH and GPG keys**  添加SSH keys
3.  将远程仓库代码、文件克隆到本地:`git clone [远程仓库地址]` 
4. 将本地内容推送到 **github** 仓库下命令
   * `git remote add origin (你仓库的 ssh 或者 https 地址)`
   * **注意：** 第一次推送时 **github** 上的仓库并非是空的，他们默认创建一个 **README** 的文档，因此需要将两者进行合并。<br> 语法：`git pull --rebase origin master` 
5. 更本地代码
   * `git push origin master`  提交本地代码到远程仓库



### 二 . GIT常用命令

* `git remote -v`  查看远端地址
* `git config --list`  查看配置
* `git remote remove origin`  删除本地远程仓库
* `git remote add origin (远程仓库地址) `  连接远程仓库
* `git remote set-url origin (远程仓库地址)`  重新设置（修改）远程仓库地址
* `git push -u(第一次要用-u 以后不需要) orgin master`  把当前分支推送到远程仓库
* `git push origin master`  git 会把master分支推送到远程git仓库上
* `git push origin_new master`  重新推送
* `git clone [远程仓库地址]`  将远程仓库代码克隆到本地
* `git clone <版本的网址> <本地目录名>`  本地目录与远程目录不同名设置
* `git pull`  更新本地代码
* `git pull <远程主机名> <远程分支名>:<本地分支名>`   本地目录与远程目录不同名设置
* `git rm (文件名)`  删除文件
* `git rm -r (文件夹名)`  删除本地文件夹
* `git status`   查看当前仓库状态
* `git branch`  查看本地分支
* `git branch -r`   查看远程分支
* `git branch -a`   查看所有分支
* `git checkout [分支名称]`  切换分支



### 三. 命令行常用命令

* `rm (文件名)` 删除本地文件
* `rm -r (文件夹名)`  删除本地文件夹
* `ll -al`  查看当前文件夹中所有文件包括隐藏文件
* `cd (文件夹名)`   进入当前文件夹
* `cd ..`  退回到上级目录
* `vim config`  进入vim模式  可以编辑文件内容



### 四. 常见问题记录

### 4.1 放弃本地修改，远程仓库覆盖本地

* `git fetch --all`  只是下载代码到本地，不进行合并操作
* `git reset --hard origin/master`   把HEAD指向最新下载的版本

#### 4.2  多词提交报错导致 git (master|REBASE 1/2) 

* 回退提交，`git rebase --abort` ，解决

#### 4.3 git clone 和 git pull的区别

* `git clone` 是克隆：从远程服务器克隆一个一模一样的版本库到本地,复制的是整个版本库，叫做clone；将一个库复制到你的本地，是一个本地从无到有的过程。
  * 如果要是制定不同的目录名，可以将目录名作为git clone 命令的第二个参数。`eg：$ git clone [版本库网址] [本地目录名]`
* `git pull`是拉取：从远程服务器获取到一个branch分支的更新到本地，并更新本地库，叫做pull；指同步一个你在本地有版本的库内容更新的部分到你的本地库，作用是，取回远程主机某个分支的更新，再与本地的指定分支合并；
  * 完整格式：`git pull [远程主机（origin）] [远程分支(next)]：[本地分支(master)]` 

#### 4.4 输入 git config - -list 查看配置后如何退出

* 在最后输入 “q” 即可退出



#### 4.5 git pull成功本地代码没更新

1. 由于本地的更改所以没有拉取成功，可以这样解决：
   1. 先使用`git stash`将本地修改储存起来。
   2. 然后再`git pull` ；这里建议使用完整的命令`git pull orgin master` 



# 常用操作

## git上传如何忽略node_modules

> 参考链接：https://www.cnblogs.com/wangRong-smile/articles/11607458.html

### 一. 创建.gitignore文件

1. 点击项目文件，右键选择Git Bash进入命令行，输入touch .gitignore，生成.gitignore文件
2. 在生成的.gitignore文件里输入你要忽略的文件件及其文件即可。

### 二.配置规则：

1. /mtk/ 过滤整个文件夹，例：node_modules/
2. ip *.z 过滤zip后缀文件
3. /mtk/do.c 过滤该文件，例：demo.html
4. 前面加 ！，表示不过滤此项，例：!src/ 或者 !*.js 或者 !index.html

### 三.提交时忽略文件命令

```
git commit -m ``"xx"` `--no-verify
```





## git将自己分支代码提交到dev分支

### 简单的代码提交流程

1. git status #查看工作区代码相对于暂存区的差别
2. git add . #将当前目录下修改的所有代码从工作区添加到暂存区 . 代表当前目录 add后面一个空格然后输入点
3. git commit -m #‘注释’ 将缓存区内容添加到本地仓库
4. git commit -m “备注” #可以合并成为git commit -a -m “备注”
5. git pull #拉下git最新代码，必须要执行，不然会覆盖掉别人刚提交过的代码。
6. git push origin master #将本地版本库推送到远程服务器，
7. origin #是远程主机，master表示是远程服务器上的master分支，分支名是可以修改成其他分支 的名字的



提交代码教程

首先查看自己在那个分支如果在自己想提交的分支就无需更改

git branch -a

第一步先切换到自己想要提交的分支

git checkout dev
dev是我所要提交的分支所以先切换好

git status

git add .
执行完这一步骤下面出来得是警告不用管

git commit -m "zabbix-server_install"
执行完这一条命令之后需要你输入git得用户和密码

双引号里面写zabbix-server_install是因为我提交的是zabbix的代码


git pull origin dev

git push origin dev
dev是git上面的分支 提交的时候换成你分支的名字即可

### Git自己分支合并dev分支

```sh
git push 自己分支 (⚠️ 我这里的push 忽略了上传代码的几个步骤喔)
 git checkout dev 切换到dev分支 
 git pull dev (拉取dev最新代码)
 git merge 自己分支 (合并自己的代码到dev)
 git push dev (此时dev分支是最新的)
 git checkotut 自己分支 
 git merge dev(合并完毕)
```



### 拉取dev分支最新代码

```sh
git pull origin dev
```



# vscode用git上传代码

> 参考链接：
>
> https://blog.csdn.net/weixin_44994731/article/details/109305995
>
> https://blog.csdn.net/Miss_liangrm/article/details/98025128