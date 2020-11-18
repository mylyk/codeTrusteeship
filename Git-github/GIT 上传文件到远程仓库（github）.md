### 一 . GIT 上传文件到远程仓库（github）

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
   * `git pull <远程主机名> <远程分支名>` 



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
* `git pull`  更新本地代码
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







