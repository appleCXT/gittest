## git的使用心得
### git安装
```
Administrator@2012-20131015RQ MINGW32 ~
$ git init      //在此文件目录下生成一个本地仓库，会在此文件夹下自动生成一个.git文件，.git文件用来记录版本信息
Initialized empty Git repository in C:/Users/Administrator/.git/

Administrator@2012-20131015RQ MINGW32 ~ (master)
$ git help
usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Reapply commits on top of another base tip
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.

Administrator@2012-20131015RQ MINGW32 ~ (master)
$ git config --global user.name 'xxx'   //设置git的用户名，这里是要关联github的用户名，两者一致

Administrator@2012-20131015RQ MINGW32 ~ (master)
$ git config --global user.email 'xxxxxxxx'  //设置git的邮箱，这里是要关联github的邮箱，两者一致

Administrator@2012-20131015RQ MINGW32 ~ (master)
$ cd D:\前端\前端\git
bash: cd: D:前端-前端git: No such file or directory //文件路径不要有汉字,否则找不到该文件

Administrator@2012-20131015RQ MINGW32 ~ (master)
$ pwd //显示当前目录路径
/c/Users/Administrator


Administrator@2012-20131015RQ MINGW32 ~ (master)
$ cd D:\study-git //变化文件路径，由默认的c盘变化到d盘建立仓库

Administrator@2012-20131015RQ MINGW32 /d/study-git
$ pwd
/d/study-git

Administrator@2012-20131015RQ MINGW32 /d/study-git
$ git init //在d盘建立仓库
Initialized empty Git repository in D:/study-git/.git/

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ cd  C:/Users/Administrator/.git/

Administrator@2012-20131015RQ MINGW32 ~/.git (GIT_DIR!)
$ cd..
bash: cd..: command not found // cd后面有空格 之后在..

Administrator@2012-20131015RQ MINGW32 ~/.git (GIT_DIR!)
$ cd .. // cd后面有空格 之后在..

Administrator@2012-20131015RQ MINGW32 ~ (master)
$ rm -rf .git //删除c盘的仓库

Administrator@2012-20131015RQ MINGW32 ~
$  cd D:\study-git

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git add readme.txt //readme文件没有新建 仓库是无法找到这个文件的
fatal: pathspec 'readme.txt' did not match any files

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git add readme.txt//在D盘新建一个文件，之后用add命令添加文件到本地仓库

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git commit -m '添加文件readme'  //commit会提交所有有更改的文件
[master (root-commit) 9ce2a68] 添加文件readme
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git log //查看变化记录
commit 9ce2a68d0af462f1f24d6381bf217606e21882be (HEAD -> master)
Author: cxt <caoxueting163@163.com>
Date:   Mon Apr 2 22:44:50 2018 +0800

    添加文件readme
Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git add * //修改文件readme，之后添加

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git status //查看自己的变动
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   readme.txt


Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git commit -m 'xiugai' //提交所有变动到本地仓库，并做提交记录
[master 9ceb008] xiugai
 1 file changed, 1 insertion(+), 1 deletion(-)

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git log
commit 9ceb008683ecf7942fa3292441b182d28545773d (HEAD -> master)
Author: xxx
Date:   Mon Apr 2 22:48:12 2018 +0800

    xiugai

commit 9ce2a68d0af462f1f24d6381bf217606e21882be
Author: xxx
Date:   Mon Apr 2 22:44:50 2018 +0800

    添加文件readme

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git diff 9ce2a68d0af462f1f24d6381bf217606e21882be //与上次提交的进行差异化对比
diff --git a/readme.txt b/readme.txt
index d8036c1..d3cf301 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
 Git is a version control system.
-Git is free software.
\ No newline at end of file
+Git is free software2.
\ No newline at end of file

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git add *

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git commit -m 'tianjialiangge'
[master 30ec000] tianjialiangge
 1 file changed, 2 insertions(+)
 create mode 100644 readme - 2.txt

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git config --global user.name 'xxx'

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git config --global user.email 'xxx'

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ ssh-keygen -t rsa -C 'xxx' //生成秘钥
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa): D:\study-git
D:\study-git already exists.
Overwrite (y/n)? n //这里如果是yes 会覆盖d盘的内容

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ ssh-keygen -t rsa -C 'caoxueting163@163.com'
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa):
/c/Users/Administrator/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/Administrator/.ssh/id_rsa.
Your public key has been saved in /c/Users/Administrator/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:vp7SWv+afWBCA7vBpj/jqyqWodD1m/BP2q4NILZazkE caoxueting163@163.com
The key's randomart image is:
+---[RSA 2048]----+
|                 |
|        .        |
|       . o       |
|    .   = o      |
| .E... oS+ .     |
|.ooo..o.. . o    |
|..+o o.=+  o .   |
|.=+.  =B=+ o  .  |
|..o...=X@++oo.   |
+----[SHA256]-----+

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ ssh -T git@github.com //测试是否连接github成功
The authenticity of host 'github.com (13.229.188.59)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,13.229.188.59' (RSA) to the list of known hosts.
Hi appleCXT! You've successfully authenticated, but GitHub does not provide shell access.

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git remote add origin git@github.com:appleCXT/gittest.git //拷贝github上新建仓库的地址 与本地仓库建立连接 

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git pull origin master
Warning: Permanently added the RSA host key for IP address '13.250.177.223' to the list of known hosts.
warning: no common commits
remote: Counting objects: 3, done.
gitremote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From github.com:appleCXT/gittest
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master
  fatal: refusing to merge unrelated histories

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git push -u origin master //github新建的仓库有自带的readme文件，所以git push 会拒绝
To github.com:appleCXT/gittest.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:appleCXT/gittest.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git pull --rebase origin master //git push 被拒绝的解决方法
From github.com:appleCXT/gittest
 * branch            master     -> FETCH_HEAD
  First, rewinding head to replay your work on top of it...

Applying: 添加文件readme
Applying: xiugai
Applying: tianjialiangge

Administrator@2012-20131015RQ MINGW32 /d/study-git (master)
$ git push -u origin master  //git push 被拒绝的解决方法
Counting objects: 8, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (8/8), done.
Writing objects: 100% (8/8), 812 bytes | 29.00 KiB/s, done.
Total 8 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To github.com:appleCXT/gittest.git
   c1124ab..cfd5564  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```
