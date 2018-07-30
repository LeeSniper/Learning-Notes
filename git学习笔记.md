# git 学习笔记

## git相关知识

### git常用命令汇总

#### 1、git账号设置
- git config --global user.name "Your Name"
- git config --global user.email "Your Email"

#### 2、文件管理
- git add <file> 添加文件或者把对文件的修改添加到暂存区
- git add --all 添加所有修改到暂存区
- git commit -m 提交修改，-m之后是本次提交的说明
- git commit -s -s表示添加签名信息，就像“Signed-off-by: lixiang <lixiang@126.com>”这样
- git commit -amend
- git status 查看仓库当前状态，查看哪些文件被修改过
- git diff 查看哪些内容被修改
- git log 按照从近到远的顺序，显示提交日志
- git log --pretty=oneline 单行显示提交日志
- git reset --hard HEAD^ 回退到上一版本，^^回退两个版本
- git reset --hard <版本号>  回退到指定版本，可以通过log查看版本号
- git checkout -- <file> 可以在提交之前舍弃对工作区文件的修改
- git reset HEAD <file> 撤销对暂存区文件的修改
- git reflog 记录每一次命令操作

#### 3、分支管理
- git remote -v	查看远程服务器地址和仓库名称
- git remote show origin	查看远程服务器仓库状态
- git remote add <name> git@server-name:path/repo-name.git 关联一个远程库
- git remote set-head origin master 设置远程仓库的HEAD指向master分支
- git remote set-url <name> git@server-name:path/repo-name.git	设置远程仓库地址（用于修改远成仓库地址）
- git remote rm git@server-name:path/repo-name.git	删除远程仓库
- git clone git@server-name:path/repo-name.git 克隆一个本地库
- git push -u origin master 把当前本地库推送到空的远程库，-u会把本地分支和远程分支相关联
- git push origin master 把本地分支推送到远程库
- git push origin HEAD:feature/V2.0.1
- git push origin HEAD:refs/for/master 提交到 gerrit 上面
- git branch 查看本地所有分支
- git branch <name> 新建本地分支
- git branch -a 查看本地和远程的所有分支
- git branch -r 查看所有远程分支
- git branch -av 查看本地和远程的所有分支和详细信息
- git branch -d <name> 删除该分支
- git branch --set-upstream-to=<destiny> <yourbranch>
- git branch --set-upstream-to=origin/<branch> feature/setting
- git checkout <name> 切换分支
- git checkout -b <name> 创建并切换分支
- git checkout -b <name> origin/dev 创建对应远端dev分支的本地分支
- git merge <name> 将命令中的分支合并到当前所在的分支
- git merge --no-ff dev 用非快速合并的方式合并分支

- git log --graph 查看分支合并图

#### 4、暂存管理
- git stash	暂存
- git stash list	列出所有 stash 的进度列表
- git stash pop 	恢复最新的进度到工作区（工作区和暂存区都恢复到工作区）
- git stash pop --index 恢复最新的进度到工作区和暂存区（尝试将原来暂存区的改动还恢复到暂存区）
- git stash apply	恢复暂存的内容，但是不删除进度，此外和 pop 命令一样
- git stash drop [stash_id]	删除一个进度
- git stash clear 	删除所有进度

## commit 之后如何修改
#### 修改上一个提交
如果要修改最近的一个提交，只需要使用
- git commit --amend

#### 修改之前的提交（例如倒数第二个提交）
1、使用 git rebase -i 需要修改的之前一个提交
2、执行命令之后，将需要修改的提交前面的 pick 改成 edit
3、修改你要修改的内容，用 git commit --amend 提交修改
4、执行 git rebase --continue 恢复后面的提交

## fork之后进行代码同步

1，列出远程仓库的目录  git remote -v 默认clone后远程仓库的名字为origin，这是fork之后的项目。

2，与原项目进行关联  git remote add upstream <原项目地址>，这样就为本地的代码添加了原项目作为远程仓库，名字为upstream

3，将原项目的更新同步到本地  git fetch upstream 从原项目获取更新，放到upstream/master分支上，
本地切换到master分支上  git checkout master  
将upstream/master分支和本地的master分支合并   git merge upstream/master
将本地同步过后的代码push到GitHub上。


## git flow相关知识
### git flow常用命令汇总
- git flow init ：git flow初始化，设置master和develop分支
- git flow init -f 强制更改设置git flow初始化信息
- git config --global push.default matching
- git add .
- git cherry-pick 
- git log .





## git SubModule的使用

#### 1、为项目添加submodule

- git submodule add 远程仓库地址  添加的目录名
- git submodule add 远程仓库地址 -b 需要关联的submodule远程仓库的分支

clone项目的时候，如果包含submodule，需要执行

- git submodule init
- git submodule update
- git submodule update --init --rescursive

#### 2、submodule子项目的更新

更新项目的时候要特别注意子项目是否有更新，如果submodule有更新，可以在主项目中执行

- git submodule update

如果submodule中还依赖着别的submodule，则可以用

- git submodule foreach "git submodule update"

或者，如果主项目没有变更，则可以进入submodule的目录，直接

- git pull

如果submodule还依赖着别的submodule，则可以

- git submodule foreach "git pull"
- git submodule foreach "git pull" --rescursive

#### 3、submodule的修改

如果在添加和克隆的时候submodule没有指定对应的分支，submodule的HEAD默认是处于游离状态的，那么在进行修改的时候必须先切换到指定分支，然后才可以对submodule进行修改和提交。也可以在.gitmodules中指定所跟踪的分支，高版本的git可以用以下语句来跟踪远程分支。

- git submodule update --remote
- git submodule update --remote --rescursive

修改完submodule之后，需要在submodule内做一次提交，之后回到主项目目录层级再做一次提交，否则会引起git仓库的版本错乱。

如果修改的时候忘记将submodule切换到远程跟踪分支，并且做了提交，可以通过以下步骤进行挽救。先切换到远程跟踪分支，根据上次提交的changeid拾取没有在branch上的提交，然后重新提交到远程跟踪分支上。

- git checkout master
- git cherry-pick 需要找回的changeid
- git push

#### 4、submodule的删除

先到项目目录下清理submodule文件，然后删除git中记录的相关数据，随后将变更提交到远程仓库。

[关于submodule的更多讲解](http://easior.is-programmer.com/posts/42541.html)

[使用Git Submodule可能遇到的坑](http://mobile.51cto.com/aprogram-393324.htm)

[参考文章1](http://blog.csdn.net/d_clock/article/details/43602699)

[参考文章2](http://blog.csdn.net/d_clock/article/details/43730449)


## SSH Key
生成 SSH Key

	ssh-keygen -t rsa
	cat ~/.ssh/id_rsa.pub


## git 快捷键设置

### git 配置文件

- 仓库级配置文件：位于当前仓库下，只对当前仓库生效
- 全局级配置文件：
- 系统级配置文件：

#### git config 命令查看配置文件

	git config [--local|--global|--system] -l #[]中的参数设置查看的配置文件的级别，-l 是 -list 的缩写

#### git config 命令修改配置文件
修改单条配置

	git config --global alias.s status #代表输入git s就代表git status
	
修改配置文件

	git config [--local|--global|--system] -e #[]内的参数同上，-e 是 -edit 的缩写，打开文件之后按键盘上的 I 键就可以输入，修改完之后按 Esc 退出编辑，输入 ：wq 保存退出。
