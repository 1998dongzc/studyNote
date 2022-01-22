# Git命令

### 1. git clone指令

```git
git clone Url(仓库项目的Http路径 如http://xxx/projectName/xxx.git) 
```

> 将项目从代码仓库克隆到本地中。



### 2.git branch指令

```shell
git branch

$ git branch
  bugFix
* maint
  master
```

> 查看本地当前所有分支。



```shell
git branch -d <branchName>

$ git branch -d bugFix
Deleted branch bugFix (was 44d1ff1).
$ git branch
* maint
  master
```

> 根据分支名删除指定分支。



```shell
git branch -r
```

>查看所有远程分支。



### 3.git checkout指令

```
git checkout <branchName>|<commitId>|HEAD~<nums>|HEAD^|<fileName>|<fileDir>

$ git checkout master
Switched to branch 'master'
```

> git checkout <branchName>：  切换指定分支
>
> git checkout <commitId>：  切换到指定CommitId的Commit
>
> git checkout HEAD~<nums>：  切换到指定HEAD前nums次的Commit
>
> git checkout HEAD^：  切换到上次Commit
>
> git checkout <fileName>：  取消fileName文件的修改
>
> git checkou<fileDir>：  取消fileDir文件夹的修改



```
git checkout -b <branchName>

$ git checkout -b test
Switched to a new branch 'test'

//新下拉的项目
git checkout -b <本地分支名> <远程主机>:<远程分支名>
```

> 切换分支，如果branchName不存在 先创建branchName再切换分支。
>
>  
>
> 新下拉的项目 且已经存在某个分支 使用该命令 将远程仓库的指定分支映射对应到本地分支



### 4.git 提交相关操作

```
git log 查看提交记录日志。

git log --graph --decorate --oneline --all 查看分支图

git config --global alias.lg "log --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative" 将查看git分支图的命令 赋予git lg指令封装（可以通过修改alias.后的内容修改命令名）
```



```shell
git status
git status -s //获取简短的结果

$ git status -s
A  .idea/vcs.xml
 M .idea/workspace.xml
 
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .idea/vcs.xml

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   .idea/workspace.xml
```

> 查看距上次提交哪些文件被操作 

```shell
git diff //查看所有文件改动内容 工作区与暂存区相比
git diff <文件名> //查看指定文件改动内容 工作区与暂存区相比
git diff --cached //查看已缓存文件改动内容 暂存区与上次提交相比
git diff --cached <文件名> //查看已缓存指定文件改动内容 暂存区与上次提交相比
git diff <commitID> 查看指定commitId的commit对比
git diff HEAD^ 查看上次Commit的对比
git diff HEAD~<nums> 查看指定第前nums的commit的对比

$ git diff src/test.java
diff --git a/src/test.java b/src/test.java
index ba60e88..fa63151 100644
--- a/src/test.java
+++ b/src/test.java
@@ -2,6 +2,7 @@ public class test {

     public static void main(String[] args) {
         System.out.println("hello world");
+        System.out.println(hhhh);^M
     }

 }
```

> 查看距上次提交文件被修改内容



```shell
git add . //所有文件
git add <文件名> //指定文件
git add ./路径名/*.java //指定路径下所有的java文件
git add ./路径名/* //指定路径下所有文件
```

>将工作目录所有文件提交到git暂存区，可以根据参数选择指定文件。



```shell
git rm --cache <fileNmae>|<fileDir> 将文件|文件夹移除暂存区
```

|用于取消git add某一文件或文件夹目录的后操作



```shell
git commit -m "提交描述内容" 

$ git commit -m "提交测试"
commit 059f6eabc58b0463463a24a5ea0e5acbd76ecf6e (HEAD -> master)
Author: 董政辰 <zcdong@email.com>
Date:   Thu Apr 8 15:11:12 2021 +0800

    提交测试
```

>发起一次提交 并对提交进行描述。



```shell
git reset HEAD~1

$ git log
commit bd8b721696d24da9bd2c650e9359e1f024f2292a (HEAD -> master)
Author: 董政辰 <zcdong@email.com>
Date:   Thu Apr 8 15:15:08 2021 +0800

    二次提交

commit 059f6eabc58b0463463a24a5ea0e5acbd76ecf6e
Author: 董政辰 <zcdong@email.com>
Date:   Thu Apr 8 15:11:12 2021 +0800

    提交测试


$ git reset HEAD~1
Unstaged changes after reset:
M       .idea/workspace.xml

$ git log
commit 059f6eabc58b0463463a24a5ea0e5acbd76ecf6e (HEAD -> master)
Author: 董政辰 <zcdong@email.com>
Date:   Thu Apr 8 15:11:12 2021 +0800

    提交测试
```

> 取消上一次的提交 如果取消多次提交可以将数字1修改成对应的次数 
>
> 若过添加--hard参数会删除本地磁盘中的修改内容
>
> 与git checkout同样 可以选择 commitId|HEAD~<nums>|HEAD^等选择指定提交操作



```shell
git revert HEAD
```

>取消上次提交内容，但不会删除被取消的提交 而是新提交与上次提交前一样的内容。
>
>与git checkout同样 可以选择 commitId|HEAD~<nums>|HEAD^等选择指定提交操作



### 5.branch操作

```shell
git merge|rebase <分支名>
```

> 将当前分支与指定进行合并，rebase与merge的不同在于:
>
> merge-会在两个分支中生成一个新提交节点，此节点指向合并前的两个提交父节点，能清楚的表示出所有提交记录。
>
> rebase-会将指定节点直接复制到本分支节点下，并“删除”掉合并前的提交，使提交历史变得清晰简单。



```shell
git cherry-pick <提交ID><提交ID><提交ID>...
```

> 根据Commit的hashId来顺序复制存放到本分支节点下。



### 6.Git远程操作

```shell
git fetch
```

> 更新远程库的分支和代码，但不修改本地工作磁盘中的内容。



```shell
git pull
```

> 等效于git fetch+git merge两个命令的总结，先更新远程分支提交记录，再更新本地工作目录中文件内容，git pull产生冲突时，手动解决冲突。



```shell
git push
git push <远程主机名> <本地分支名>:<远程分支名>
git push <远程主机名> <本地分支名>  //前提要求 本地分支名与远程分支名一样
```

> 将本地提交，上传至远程代码库中。指令中可以指定上传的远程分支

```shell
git push --force 强制将本地分支覆盖到远程分支
```

> 用于上传至git仓库后 想要撤回这一远程代码的提交
>
> 先用git reset --soft 取消回退到push错误的某一个本地commit
>
> 在使用git push --force强行覆盖远程仓库 即可取消远程仓库的代码提交

