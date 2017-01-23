###创建版本库
>1.选择一个合适的地方，创建一个空目录：
````
$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit
````
2.通过git init命令把这个目录变成Git可以管理的仓库。
  用ls -ah命令可以查看隐藏目录。  

####把一个文件放到Git仓库
>1.用命令git add告诉Git，把文件添加到仓库。  
2.用命令git commit告诉Git，把文件提交到仓库。

>或者使用git citool来操作。

### 时光机穿梭
>1.git status 查看变化  
2.git diff   比较差别  
3.git log命令显示从最近到最远的提交日志,可以试试加上--pretty=oneline参数


####版本回退
>1.Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。  
2.git reset --hard 想要恢复的commit id  
3.git reflog 用来记录你的每一次命令

####撤销修改
>命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：  
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；  
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。  
总之，就是让这个文件回到最近一次git commit或git add时的状态。
