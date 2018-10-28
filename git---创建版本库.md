**创建版本库**
**概述**
(1)初始化一个Git仓库，使用`git init`命令。
(2)添加文件到Git仓库，分两步：
使用命令`git add <file>`，注意，可反复多次使用，添加多个文件；
使用命令`git commit -m <message>`，完成。


**1.创建一个版本库**
(1)选择一个合适的地方，创建一个空目录：
```
mkdir learngit
cd learngit
 pwd
/Users/michael/learngit
```
pwd命令用于显示当前目录

(2)通过git init命令把这个目录变成Git可以管理的仓库：
```
git init
Initialized empty Git repository in /Users/michael/learngit/.git/
```
如果你没有看到.git目录，那是因为这个目录默认是隐藏的，用ls -ah命令就可以看见。

**2.把一个文件放到Git仓库**

(1)第一步，用命令git add告诉Git，把文件添加到仓库：
```
$ git add readme.txt
```
执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

(2)第二步，用命令git commit告诉Git，把文件提交到仓库：
```
$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
 ```

`git commit`命令执行成功后会告诉你，
1` file changed`：1个文件被改动（我们新添加的readme.txt文件）；
2 `insertions`：插入了两行内容（readme.txt有两行内容）。

(3)为什么Git添加文件需要add，commit一共两步呢？因为commit可以一次提交很多文件，所以你可以多次add不同的文件，比如：
```
$ git add file1.txt
$ git add file2.txt file3.txt
$ git commit -m "add 3 files.
```