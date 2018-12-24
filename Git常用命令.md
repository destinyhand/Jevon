# Git常用操作命令：

## 一、配置Git：

### 1、配置全局级的config

    配置用户名：git config --global user.name "你的名字"
    配置e-mail：git config --global user.email "你的邮箱@xx.com"

### 2、配置仓库级的config

    配置用户名：git config --local user.name "你的名字"
    配置e-mail：git config --local user.email "你的邮箱@xx.com"

### 3、配置系统级的config

    配置用户名：git config --system user.name "你的名字"
    配置e-mail：git config --system user.email "你的邮箱@xx.com"

>查看配置信息：

    git config --local -l

    git config --global -l

    git config --system -l

## 二、远程仓库(remote)相关命令：

    1、检出仓库：$ git clone git://github.com/jquery/jquery.git

    2、查看远程仓库：$ git remote -v

    3、添加远程仓库：$ git remote add [name] [url]

    4、删除远程仓库：$ git remote rm [name]

    5、修改远程仓库：$ git remote set-url --push [name] [newUrl]

    6、拉取远程仓库：$ git pull [remoteName] [localBranchName]

    7、推送远程仓库：$ git push [remoteName] [localBranchName]

>如果想把本地的某个分支test提交到远程仓库，并作为远程仓库的master分支，或者作为另外一个名叫test的分支，如下：

    $git push origin test:master         // 提交本地test分支作为远程的master分支
    $git push origin test:test              // 提交本地test分支作为远程的test分支

## 三、分支(branch)相关命令：

    1、查看本地分支：$ git branch

    2、查看远程分支：$ git branch -r

    3、创建本地分支：$ git branch [name] ----注意新分支创建后不会自动切换为当前分支

    4、切换分支：$ git checkout [name]

    5、创建新分支并立即切换到新分支：$ git checkout -b [name]

    6、删除分支：$ git branch -d [name] ---- -d选项只能删除已经参与了合并的分支，对于未有合并的分支是无法删除的。如果想强制删除一个分支，可以使用-D选项

    7、合并分支：$ git merge [name] ----将名称为[name]的分支与当前分支合并

    8、创建远程分支(本地分支push到远程)：$ git push origin [name]

## 四、版本(tag)操作相关命令

    1、查看版本：$ git tag

    2、创建版本：$ git tag [name]

    3、删除版本：$ git tag -d [name]

    4、查看远程版本：$ git tag -r

    5、创建远程版本(本地版本push到远程)：$ git push origin [name]

    6、删除远程版本：$ git push origin :refs/tags/[name]

    7、合并远程仓库的tag到本地：$ git pull origin --tags

    8、上传本地tag到远程仓库：$ git push origin --tags

    9、创建带注释的tag：$ git tag -a [name] -m 'yourMessage'

## 常用操作：

### 1、先有本地库，后有远程库，将本地库推送到远程库

    第一次将本地仓库推送到远程库：git push –u origin master

### 2、先有远程库，后有本地库，从远程库clone到本地库

    git clone 网站上的仓库地址

### 3、分支操作

    查看分支：git branch
    创建分支：git branch 分支名称 ----从当前分支创建
    切换分支：git checkout 分支名称
    创建并切换分支：git checkout -b 分支名称
    删除分支：git branch -d 分支名称
    合并分支：git merge 分支名称 ----从[分支名称]合并到当前分支
    查询分支状态：git status

### 4、添加文件到缓存区

    添加单个文件：git add 文件名称
    添加某文件夹下的文件：git add 文件夹名称/文件名称
    添加所有修改或删除的文件：git add -A
    查看所有修改或删除但没有提交的文件：git add -i

>提交某文件夹下的所有txt文件：

    git add 文件夹名称/*.txt

### 5、将缓存区文件提交到仓库

    git commit -m "描述"

### 6、从远程仓库拉取文件

    git pull origin 分支名称

例：git pull origin master
*表示，将 **origin**主机的 **master**分支。拉取到本地仓库的 **master**分支。如果 **master**不存在，则会被新建。*

### 7、将本地仓库推送到远程服务器

    git push origin 分支名称

例：git push origin master
*表示，将本地的 **master**分支推送到 **origin**主机的 **master**分支。如果 **master**不存在，则会被新建。*

### 8、撤销和退回

    撤销工作区的修改：git checkout -- 文件名
    撤销暂存区的修改：git reset HEAD 文件名
    回退到历史版本：git reset --hard 该版本ID
    回退到上个版本：git reset --hard HEAD^
    上上版本是HEAD^^，也可用HEAD~2表示，以此类推

### 9、比较和查看

    比较文件差异（请在git add之前使用）：git diff 文件名
    查看仓库历史记录(详细)：git log
    查看仓库历史记录(单行)：git log --pretty=online 或 git log --online
    查看所有版本的commit ID：git reflog