###标签管理
>命令git tag <name>用于新建一个标签，默认为HEAD，也可以指定一个commit id；  
git tag -a <tagname> -m "blablabla..."可以指定标签信息；  
用命令git show <tagname>可以看到说明文字：

>命令git push origin <tagname>可以推送一个本地标签；  
命令git push origin --tags可以推送全部未推送过的本地标签；  
命令git tag -d <tagname>可以删除一个本地标签；  
命令git push origin :refs/tags/<tagname>可以删除一个远程标签。  

>使用Windows的童鞋注意了，如果你在资源管理器里新建一个.gitignore文件，它会非常弱智地提示你必须输入文件名，但是在文本编辑器里“保存”或者“另存为”就可以把文件保存为.gitignore了。

>忽略某些文件时，需要编写.gitignore；  
.gitignore文件本身要放到版本库里，并且可以对.gitignore做版本管理！  
可以用git check-ignore命令检查到底哪个规则写错了：

####配置别名  
>git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"  
配置Git的时候，加上--global是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用。  
别名就在[alias]后面，要删除别名，直接把对应的行删掉即可。
而当前用户的Git配置文件放在用户主目录下("C:\Users\用户名")的一个隐藏文件.gitconfig中：  
配置别名也可以直接修改这个文件，如果改错了，可以删掉文件重新通过命令配置。
