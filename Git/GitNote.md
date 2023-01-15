## Git概述 ##
Git 是免费，开源的分布式版本控制系统，可以快速高效地处理从小型到大型的各种项目。易于学习，占地面积小，性能快。具有廉价的本地库，方便的暂存区，和多个工作流分支等特性。
### Git 和代码托管中心 ###
代码托管中心是基于网络服务器的远程代码仓库，称为远程库。
局域网 GitLab
互联网 GitHub Gitee
### 常用命令 ###
| 命令名称 | 作用 |
| :-----: | :-----:|
| git config --global user.name| 设置用户名|
| git config --global user.email | 设置邮箱 |
| git init | 初始化本地库 |
| git status | 查看本地库状态 |
| git add 文件名 | 文件添加到暂存区 |
| git commit -m 日志信息 文件名 | 提交到本地库 |
| git reflog 版本号| 查看版本信息 |
| git log | 查看版本详细信息 |
| git reset --hard 版本号 | 版本穿梭 |
```git
git config --global user.name yyk
git config --global user.email 1234567@qq.com
//签名区分不同操作者，在提交信息可以看到，首次安装必须设置签名，签名信息与GitHub账号无关

git commit -m "第一次提交" hello.txt
git reset --hard 5af531f
//先查看版本号，再穿梭
```
## 分支 ##
在版本控制过程中，同时推进多个任务，为每个任务我们就可以创建每个任务的单独分支。使用分支时意味着程序员可以把自己的工作从开发主线上分离开来，开发自己分支时，不会影响主线分支运行。

并行推进多个功能开发，提高开发效率
### 分支操作 ###
| 命令名称 | 作用 |
| :-----: | :-----:|
| git branch 分支名 | 创建分支 |
| git branch -v | 查看分支 |
| git checkout 分支名 | 切换分支 |
| git merge 分支名 | 把指定分支合并到当前分支上 |
```git
git branch -v
git branch hot-fix
git checkout hot-fix
git merge hot-fix
```
### 冲突 ###
git merge + 分支名 把分支加到当前分支上，内容不同产生冲突，表现为merging，必须人为解决新代码。
<<<<<<< HEAD 
当前分支代码
\=\=\=\=\=\=\=
合并过来的代码
\>>>>>>>
新分支代码

解决冲突
1 编辑有冲突文件，删除特殊符号，决定要使用的内容
2 添加到暂存区
3 执行提交（此时git commit 命令不带文件名，不带日志信息）
## Git团队协作机制 ##
![Git团队协作](D:\stu\Note\Git\Image1.png)
创建远程仓库 New repository
输入仓库名，默认创建即可

### 远程仓库操作 ###
| 命令名称 | 作用 |
| :-----: | :-----: |
| git remote -v | 查看当前所有远程地址别名 |
| git remote add 别名 远程地址 | 起别名 |
| git push 别名 分支 | 推送 本地分支上内容到远程仓库 |
| git clone 远程地址 | 将远程仓库的内容克隆到本地 |
| git pull 远程库地址别名 远程分支名 | 将远程库对于分支最新内容拉下来后与当地本地分支直接合并 |
```git
git remote -v
git remote add ori http://github.com/....
git push ori master
git clone https://github.com/....
//克隆结果——1 拉取代码 2 初始化本地仓库 3 创建别名(文件夹)
```
![HTTPS](D:\stu\Note\Git\Image2.png)
### 邀请加入团队 ###
1 选择邀请合作者
![invite](D:\stu\Note\Git\Image3.png)
2 填入想要合作的人
![person](D:\stu\Note\Git\Image4.png)
3 复制地址并发送给用户
![adress](D:\stu\Note\Git\Image5.png)
4 收到邀请连接，点击接受邀请
![accept](D:\stu\Note\Git\Image6.png)
5 成功之后可以看到远程仓库
### 跨团队协作 ###
1 将远程仓库的地址复制发送给邀请跨团队协作的人
2 地址栏复制收到的链接，Fork将项目叉到自己本地仓库，成功后可以查看当前仓库信息
![fork](D:\stu\Note\Git\Image7.png)
![information](D:\stu\Note\Git\Image8.png)
3 可以在线编辑叉取的文件
![mark](D:\stu\Note\Git\Image9.png)
4 编辑完成后，填写描述信息并点击绿色按钮提交
![](D:\stu\Note\Git\Image10.png)
5 点击pull请求，并创建新请求
![](D:\stu\Note\Git\Image11.png)
![](D:\stu\Note\Git\Image12.png)
6 主账号可以看到pull request请求，进入聊天室可以讨论代码相关内容
![](D:\stu\Note\Git\Image13.png)
7 没有问题，主账号点击Merge pull reque合并代码，可以填写对代码描述
![](D:\stu\Note\Git\Image14.png)
### SSH免密登录 ###
