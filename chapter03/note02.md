### 远程仓库
1.push an existing repository from the command line
git remote add origin https://github.com/smallbear1986/lreangit.git
git push -u origin master
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样：

2.git push origin master把本地master分支的最新修改推送至GitHub.  
3.git 常用分支命令  
查看分支：git branch  
创建分支：git branch <name>  
切换分支：git checkout <name>  
创建+切换分支：git checkout -b <name>  
合并某分支到当前分支：git merge <name>  
删除分支：git branch -d <name>

4.通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
准备合并dev分支，请注意--no-ff参数，表示禁用Fast forward：  
git merge --no-ff -m "merge with no-ff" dev

5.用git stash list命令查看暂存区历史，需要恢复一下，有两个办法：  
一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；  
另一种方式是用git stash pop，恢复的同时把stash内容也删了：  
git stash apply stash@{0}
