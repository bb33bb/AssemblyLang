今天想把电脑上的本地项目通过`Git`提交到`Coding`上面，在`Coding`上创建项目、初始化仓库并自动创建了`README.md`文件，然后本地提交时执行`git push`的时候，提示：

```
To https://git.coding.net/xxxx/xxx.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://git.coding.net/xxxx/xxx.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

提示`push`失败，在`push`执行需要执行`pull`拉取远程代码。然后执行`git pull origin master`：

```
From https://git.coding.net/xxxx/xxx
 * branch            master     -> FETCH_HEAD
fatal: refusing to merge unrelated histories
```

意思是拒绝合并没有联系的历史，表明本地和远程现在是两个不同的项目。

解决方案（使用其中一种即可）
**针对refusing to merge unrelated histories问题**

```
#允许合并不相关的内容
$ git pull --allow-unrelated-histories

#提交内容
$ git push 
```

**针对non-fast-forward问题**

```
#强推，本地代码强行覆盖远程`git`仓库
$ git push -f
```