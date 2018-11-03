首先，linux下安装git

在终端输入`sudo apt-get install git`

 # 这些是各种场合常见的 `Git` 命令：

(使用形式`git xxx`)

（1）开始一个工作区（参见：git help tutorial）
|  命令 | 含义  |
|---|---|
  | `clone ` |    克隆一个仓库到一个新目录|
  | `init `   |   创建一个空的 Git 仓库或重新初始化一个已存在的仓库|

 （2）在当前变更上工作（参见：git help everyday）
| 命令  |含义  |
| ---|---|
  | `add` |       添加文件内容至索引|
  | `mv`   |      移动或重命名一个文件、目录或符号链接|
   |`reset`   |   重置当前 HEAD 到指定状态|
  | `rm` |        从工作区和索引中删除文件|

（3）检查历史和状态（参见：git help revisions）
  |  命令   |  含义  |
  |:---|:----|
   |`bisect`  |   通过二分查找定位引入 bug 的提交|
 |  `grep`     |  输出和模式匹配的行|
 |  `log`       | 显示提交日志|
 |  `show`    |   显示各种类型的对象|
  | `status`   |  显示工作区状态|

（4）扩展、标记和调校您的历史记录
|   命令 | 含义   |
 |---|----|
  | `branch`  |   列出、创建或删除分支|
  | `checkout` |  切换分支或恢复工作区文件|
  | `commit`    | 记录变更到仓库|
  | `diff`    |   显示提交之间、提交和工作区之间等的差异|
  | `merge`    |  合并两个或更多开发历史|
  | `rebase`   |  在另一个分支上重新应用提交|
|`tag`     |   创建、列出、删除或校验一个 GPG签名的标签对象|

(5)协同（参见：git help workflows）
   | 命令| 含义|
   |---|---|
  | `fetch`    |  从另外一个仓库下载对象和引用|
 |  `pull`   |    获取并整合另外的仓库或一个本地|分支
   |`push`   |    更新远程引用和相关的对象|

命令 `git help -a` 和 `git help -g`显示可用的子命令和一些概念帮助。
查看 `git help <命令>` 或 `git help <概念>` 以获取给定子命令或概念的
帮助。


eg:创建版本库并放入文件
```
$ mkdir notes

$ cd notes 

$ git init
已初始化空的 Git 仓库于 /home/yfc/notes/.git/
$  sudo git clone https://github.com/SCSE-StudyGroup2018/yin.git
（别忘了sudo！！！）
正克隆到 'yin'...
...
展开对象中: 100% (20/20), 完成.
```
```
$ git checkout -b dev
切换到一个新分支 'dev'

$ code git-learning.md

$ git add git-learning.md

$ git commit -m "add yfc"
(要有-m及及说明)
[dev （根提交） 3738719] add yfc
 1 file changed, 241 insertions(+)
 create mode 100644 git-learning.md
 ```




```
$ ls
1                 id_rsa      runoob.txt    test.c  yfc.md  视频  音乐
1.c               id_rsa.pub  snap          y       yin     图片  桌面
a.out             notes       spf13-vim.sh  y.c     公共的  文档
examples.desktop  rea.md      stduying      yfc.c   模板    下载

$ cd notes 

$ git status
位于分支 dev
要提交的变更：
	修改：     git-learning.md
尚未暂存以备提交的变更：
	修改：     git-learning.md

$ git diff
...
(按q 退出)

$ git pull

$ git add git-learning.md 

$ git commit -m "modify git-learning.md"

$ git log
commit eeab24be19a6b2df73d1c369e14cb25886e5efdd (HEAD -> dev)
Author: irene <irene6yfc@gmail.com>
Date:   Sat Nov 3 16:18:46 2018 +0800
    modify git-learning.md
commit 373871988d8b66264ebc99992495a4c5e9cef82c
Author: irene <irene6yfc@gmail.com>
Date:   Sat Nov 3 16:04:40 2018 +0800
    add yfc
(按q 退出)

$ git push


```



# 工作库和版本库
1)工作区（Working Directory） 就是你在电脑里能看到的目录，

(2)版本库（Repository） 工作区有一个隐藏目录`.git`，这个不算工作区，而是Git的版本库。 Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。

(3)把文件往Git版本库里添加的时候，是分两步执行的： 
- 第一步是用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区； 
- 第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。 
- 因为我们创建Git版本库时，Git自动为我们创建了唯一一个`master`分支，所以，现在，`git commit`就是往`master`分支上提交更改。 你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。


# 版本回退
(1)要随时掌握工作区的状态，使用`git status`命令。

(2)如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容。

(3)每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为commit。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个commit恢复，然后继续工作，而不是把几个月的工作成果全部丢失。

(4)版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用`git log`命令查看,`git log`命令显示从最近到最远的提交日志，

(5)用`HEAD`表示当前版本上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个^比较容易数不过来，所以写成`HEAD~100`

(6)现在总结一下： 

HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。

穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。

要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

# 管理修改与撤销修改.
- 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。 
- 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

# 删除文件
现在你有两个选择，一是确实要从版本库中删除该文件，那就用命令`git rm`删掉，并且`git commit`：
```
$ git rm test.txt
rm 'test.txt'

$ git commit -m "remove test.txt"
[master d46f35e] remove test.txt
 1 file changed, 1 deletion(-)
 delete mode 100644 test.txt
```
另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：
```
$ git checkout -- test.txt
```
# 添加远程库
小结

要关联一个远程库，使用命令
```
git remote add origin git@server-name:path/repo-name.git；
```
关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；

此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；



# 创建与合并分支

Git鼓励大量使用分支：

查看分支：`git branch`

创建分支：`git branch <name>`

切换分支：`git checkout <name>`

创建+切换分支：`git checkout -b <name>`

合并某分支到当前分支：`git merge <name>`

删除分支：`git branch -d <name>`


# 解决冲突

当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。

用`git log --graph`命令可以看到分支合并图。

# bug 分支
`stash`可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作：
```
$ git stash
Saved working directory and index state WIP on dev: f52c633 add merge
```
现在，用`git status`查看工作区，就是干净的（除非有没有被Git管理的文件），因此可以放心地创建分支来修复bug。

首先确定要在哪个分支上修复bug，假定需要在`master`分支上修复，就从`master`创建临时分支：
```
$ git checkout master

$ git checkout -b issue-101

$ git add readme.txt 

$ git commit -m "fix bug 101"
```
修复完成后，切换到`master`分支，并完成合并，最后删除`issue-101`分支：
```
$ git checkout master

$ git merge --no-ff -m "merged bug fix 101" issue-101

$ git checkout dev

$ git status
On branch dev
nothing to commit, working tree clean

$ git stash list
stash@{0}: WIP on dev: f52c633 add merge
```
工作现场还在，Git把stash内容存在某个地方了，但是需要恢复一下，有两个办法：

一是用`git stash apply`恢复，但是恢复后，stash内容并不删除，你需要用`git stash drop`来删除；

另一种方式是用`git stash pop`，恢复的同时把stash内容也删了：

再用`git stash list`查看，就看不到任何stash内
容
你可以多次`stash`，恢复的时候，先用`git stash list`查看，然后恢复指定的stash，用命令：
```
$ git stash apply stash@{0}
```
小结

修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

当手头工作没有完成时，先把工作现场`git stash`一下，然后去修复bug，修复后，再`git stash pop`，回到工作现场。


# 推送分支

```
$ git push origin 某分支
```

 `master`分支是主分支，因此要时刻与远程同步；

  `dev`分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；

  `bug`分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；

 `feature`分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

# 分支管理策略
Git分支十分强大，在团队开发中应该充分应用

基本原则：

- 首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

- 干活都在dev分支上，每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。

- 合并分支时，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并就看不出来曾经做过合并。

# 多人协作
工作模式：

- 首先，可以试图用`git push origin <branch-name>`推送自己的修改；

 - 如果推送失败，则因为远程分支比你的本地更新，需要先用`git pull`试图合并；

- 如果合并有冲突，则解决冲突，并在本地提交；

- 没有冲突或者解决掉冲突后，再用`git push origin <branch-name>`推送就能成功！




# 创建标签

**概述**

- `git tag <tagname>`用于新建一个标签，默认为`HEAD`，也可以指定一个`commit id`；

- `git tag -a <tagname> -m "blablabla..."`可以指定标签信息；

 -  `git tag`可以查看所有标签。

- `git push origin <tagname>`可以推送一个本地标签；

- `git push origin --tags`可以推送全部未推送过的本地标签；

- `git tag -d <tagname>`可以删除一个本地标签；

 - `git push origin :refs/tags/<tagname>`可以删除一个远程标签。

（1）首先，切换到需要打标签的分支上：

然后，敲命令`git tag <name>`就可以打一个新标签：
```
$ git tag v1.0
```
可以用命令`git tag`查看所有标签：

(2）默认标签是打在最新提交的commit上的。现在已经是周五了，想要补上周一没打的标签

方法是找到历史提交的commit id，然后打上就可以了：
```
$ git log --pretty=oneline --abbrev-commit
f52c633 add merge`
```
比方说要对add merge这次提交打标签，它对应的commit id是f52c633，敲入命令：
```
$ git tag v0.9 f52c633
```
再用命令git tag查看标签：
```
$ git tag
v0.9
v1.0
```
(3)
注意，标签不是按时间顺序列出，而是按字母排序的。可以用`git show <tagname>`查看标签信息：
还可创建带有说明的标签，用`-a`指定标签名，`-m`指定说明文字：
```
$ git tag -a v0.1 -m "version 0.1 released" 1094adb
```
注意：标签总是和某个commit挂钩。如果这个commit既出现在master分支，又出现在dev分支，那么在这两个分支上都可以看到这个标签。

 # 自定义Git 
- 让Git显示颜色，会让命令输出看起来更醒目：
```
$ git config --global color.ui true
```
- 配置别名

(当然，原名与别名均可使用)
```
$ git config --global alias.st status
$ git config --global alias.co checkout
$ git config --global alias.ci commit
$ git config --global alias.br branch
$ git config --global alias.unstage 'reset HEAD'
$ git config --global alias.last 'log -1'
```
- 每个仓库的Git配置文件都放在.git/config文件中：
```
$ cat .git/config 
```
而当前用户的Git配置文件放在用户主目录下的一个隐藏文件.gitconfig中：
```
$ cat .gitconfig
```