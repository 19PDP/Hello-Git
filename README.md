这些内容是在学习廖老师的[Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)时做的笔记，总结在这里。
一方面是为了巩固学习内容；
一方面也方便后续查阅命令；
再就是对有些内容做了适当的更改，比如新版 git 推荐使用 `git switch` 和 `git restore` 替代过时的 `git checkout`......

---
>下面是各专题的命令大纲，各专题的跳转链接有详细笔记
### [安装git](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/1.%E5%AE%89%E8%A3%85git.md)

### [创建版本库](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/2.%E5%88%9B%E5%BB%BA%E7%89%88%E6%9C%AC%E5%BA%93.md)

1. 初始化一个Git仓库，使用`git init`

2. 添加文件到Git仓库，分两步：
使用`git add <file>`，注意，可反复多次使用，添加多个文件；
再使用`git commit -m <message>`

### [向仓库提交修改](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/3.%E5%90%91%E4%BB%93%E5%BA%93%E6%8F%90%E4%BA%A4%E4%BF%AE%E6%94%B9.md)

1. 要随时掌握工作区的状态，使用`git status`

2. 如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容

3. 提交修改与提交新文件一样，使用`git add`和`git commit` 

### [版本回退](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/4.%E7%89%88%E6%9C%AC%E5%9B%9E%E9%80%80.md)

1. `HEAD`指向当前版本，Git允许在不同历史版本之间穿梭，使用命令`git reset --hard commit_id`

2. 穿梭前，用`git log--pretty=oneline--abbrev-commit`查看提交历史，确定要回退到哪个版本及其版本号

3. 要重返未来，用`git reflog`查看历史命令，确定要回到未来的哪个版本

### [工作区和暂存区](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/5.%E5%B7%A5%E4%BD%9C%E5%8C%BA%E5%92%8C%E6%9A%82%E5%AD%98%E5%8C%BA.md)

### [撤销修改](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/6.%E6%92%A4%E9%94%80%E4%BF%AE%E6%94%B9.md)

1. 要丢弃工作区的修改，用`git restore readme.txt`

2. 要丢弃缓存区的修改，用`git restore --staged readme.txt`

3. 要丢弃仓库的修改，用`git reset —- hard HEAD`

### [删除文件](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/7.%E5%88%A0%E9%99%A4%E6%96%87%E4%BB%B6.md)

1. 从库中删除文件：先删除本地，然后`git rm/add`再`git commit`

2. 要恢复文件，使用`git restore`

### [使用GitHub](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/8.%E4%BD%BF%E7%94%A8GitHub.md)

1. 准备：在本地创建SSH Key，并将本地SSH公钥添加到GitHub；

2. 要**关联**一个远程库，使用`git remote add <name> git@github.com:19PDP/learngit.git`；

3. 关联后，使用`git push -u <name> master`**第一次推送**master分支的所有内容；

4. 此后，每次本地提交后，使用命令`git push <name> master`即可推送最新修改；

5. 要克隆一个仓库，首先必须知道仓库的地址，然后使用`git clone`命令克隆。

### [分支管理](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/9.%E5%88%86%E6%94%AF%E7%AE%A1%E7%90%86.md)

1. **查看分支**：`git branch`

2. 创建分支：`git branch <name>`

3. 切换分支：`git switch <name>`或者`git checkout <name>`

4. 创建+切换分支：`git switch -c <name>`或者`git checkout -b <name>`

5. **合并某分支**到当前分支：`git merge <name>`

6. **删除分支**：`git branch -d <name>`

7. 当合并分支出现冲突时，git会给出提示，并将文件内容中不同分支中冲突的部分标识出来。
解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。

8. 用`git log --graph`命令可以看到分支合并图。

9. 合并分支时，**加上**`--no-ff`**参数**可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并看不出来曾经做过合并。

### [标签管理](https://github.com/19PDP/Hello-Git/blob/master/Hello%20Git/10.%E6%A0%87%E7%AD%BE%E7%AE%A1%E7%90%86.md)

1. 命令`git tag <tagname>`用于新建一个标签，默认为`HEAD`，也可以指定一个commit id；

2. 命令`git tag -a <tagname> -m "blablabla..."`可以指定标签信息；

3. 命令`git tag`可以查看所有标签。

4. 命令`git push origin <tagname>`可以推送一个本地标签；

5. 命令`git push origin --tags`可以推送全部未推送过的本地标签；

6. 命令`git tag -d <tagname>`可以删除一个本地标签；

7. 命令`git push origin :refs/tags/<tagname>`可以删除一个远程标签。
