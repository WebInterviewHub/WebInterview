##Git
* [1.列举工作中常用的几个git命令？](#1列举工作中常用的几个git命令) 
* [2. 提交时发生冲突，你能解释冲突是如何产生的吗？你是如何解决的？](#2-提交时发生冲突你能解释冲突是如何产生的吗你是如何解决的)
* [3. 如果本次提交误操作，如何撤销？](#3-如果本次提交误操作如何撤销)
* [4. 如果我想修改提交的历史信息，应该用什么命令？](#4-如果我想修改提交的历史信息应该用什么命令)
* [第二步：执行命令git rebase –i HEAD~3，会把前3次的提交记录按照倒叙列出来；](#第二步执行命令git-rebase-i-head3会把前3次的提交记录按照倒叙列出来)
* [5. 你使用过git stash命令吗？你一般什么情况下会使用它？](#5-你使用过git-stash命令吗你一般什么情况下会使用它)
* [6. 如何查看分支提交的历史记录？查看某个文件的历史记录呢？](#6-如何查看分支提交的历史记录查看某个文件的历史记录呢)
* [7. 能不能说一下git fetch和git pull命令之间的区别？](#7-能不能说一下git-fetch和git-pull命令之间的区别)
* [8. 使用过git merge和git rebase吗？它们之间有什么区别？](#8-使用过git-merge和git-rebase吗它们之间有什么区别)
* [9. 能说一下git系统中HEAD、工作树和索引之间的区别吗？](#9-能说一下git系统中head工作树和索引之间的区别吗)
* [10. 之前项目中是使用的GitFlow工作流程吗？它有什么好处？](#10-之前项目中是使用的gitflow工作流程吗它有什么好处)
* [11. 使用过git cherry-pick，有什么作用？](#11-使用过git-cherry-pick有什么作用)
* [12. git跟其他版本控制器有啥区别？](#12-git跟其他版本控制器有啥区别)
* [13.我们在本地工程常会修改一些配置文件，这些文件不需要被提交，而我们又不想每次执行git status时都让这些文件显示出来，我们该如何操作？](#13我们在本地工程常会修改一些配置文件这些文件不需要被提交而我们又不想每次执行git-status时都让这些文件显示出来我们该如何操作)
* [14. 如何把本地仓库的内容推向一个空的远程仓库？](#14-如何把本地仓库的内容推向一个空的远程仓库)
* [15.如在 Git 恢复先前的提交?](#15如在-git-恢复先前的提交)
* [16.什么是“git cherry-pick”?](#16什么是git-cherry-pick)
      
#### 1.列举工作中常用的几个git命令？

新增文件的命令：git add file或者git add .

提交文件的命令：git commit –m或者git commit –a

查看工作区状况：git status –s

拉取合并远程分支的操作：git fetch/git merge或者git pull

查看提交记录命令：git reflog

#### 2. 提交时发生冲突，你能解释冲突是如何产生的吗？你是如何解决的？

开发过程中，我们都有自己的特性分支，所以冲突发生的并不多，但也碰到过。诸如公共类的公共方法，我和别人同时修改同一个文件，他提交后我再提交就会报冲突的错误。
发生冲突，在IDE里面一般都是对比本地文件和远程分支的文件，然后把远程分支上文件的内容手工修改到本地文件，然后再提交冲突的文件使其保证与远程分支的文件一致，这样才会消除冲突，然后再提交自己修改的部分。特别要注意下，修改本地冲突文件使其与远程仓库的文件保持一致后，需要提交后才能消除冲突，否则无法继续提交。必要时可与同事交流，消除冲突。
发生冲突，也可以使用命令。

- 通过git stash命令，把工作区的修改提交到栈区，目的是保存工作区的修改；
- 通过git pull命令，拉取远程分支上的代码并合并到本地分支，目的是消除冲突；
- 通过git stash pop命令，把保存在栈区的修改部分合并到最新的工作空间中；

#### 3. 如果本次提交误操作，如何撤销？

如果想撤销提交到索引区的文件，可以通过git reset HEAD file；如果想撤销提交到本地仓库的文件，可以通过git reset –soft HEAD^n恢复当前分支的版本库至上一次提交的状态，索引区和工作空间不变更；可以通过git reset –mixed HEAD^n恢复当前分支的版本库和索引区至上一次提交的状态，工作区不变更；可以通过git reset –hard HEAD^n恢复当前分支的版本库、索引区和工作空间至上一次提交的状态。

#### 4. 如果我想修改提交的历史信息，应该用什么命令？

如果修改最近一次提交的历史记录，就可以用git commit –amend命令；vim编辑的方式；
如果修改之前提交的历史记录，就需要按照下面的步骤：
第一步：首先查看前三次的提交历史记录：

```
$ git log -3
commit a762fcafecbd92bbde088054644e1b0586589c4b (HEAD -> slave)
Author: 18073638 <18073638@cnsuning.com>
Date:   Sat Mar 30 10:58:44 2019 +0800

    four commit

commit eedbc93d58780f63dd47f8388f8217892096e89a
Author: 18073638 <18073638@cnsuning.com>
Date:   Thu Mar 28 17:19:52 2019 +0800

    third commit third commit

commit 05396135eba85140602107e01e5c211d74f6c739
Author: 18073638 <18073638@cnsuning.com>
Date:   Thu Mar 28 16:56:19 2019 +0800

    second commit
```

注意：这里我们想把053961的committer对象信息修改为“second commit second commit”.

#### 第二步：执行命令git rebase –i HEAD~3，会把前3次的提交记录按照倒叙列出来；

```
pick 0539613 second commit
pick eedbc93 third commit third commit
pick a762fca four commit

# Rebase c8d7ad7..a762fca onto c8d7ad7 (3 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

这里把第一行的‘pick’修改为‘edit’，然后esc + :wq退出vim编辑器；

```
\$ git rebase -i HEAD~3
Stopped at 0539613...  second commit
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue
```

第三步：根据提示，执行git commit –amend命令，进入vim编辑器并修改提交信息。

```
$ git commit --amend
[detached HEAD 20fe643] second commit second commit
 Date: Thu Mar 28 16:56:19 2019 +0800
 1 file changed, 1 insertion(+)
```

第四步：然后执行git rebase –continue命令

```
$ git rebase --continue
Successfully rebased and updated refs/heads/slave.
```

查看修改结果

```
$ git log -3
commit 9024049ef990e79fa61295d5c2b64d70017cf412 (HEAD -> slave)
Author: 18073638 <18073638@cnsuning.com>
Date:   Sat Mar 30 10:58:44 2019 +0800

    four commit

commit 79cb4e26dd300591e6352d0488802f43b65c8ba2
Author: 18073638 <18073638@cnsuning.com>
Date:   Thu Mar 28 17:19:52 2019 +0800

    third commit third commit

commit 20fe643cbf80cdcc649d732065e8ebf4caf773c7
Author: 18073638 <18073638@cnsuning.com>
Date:   Thu Mar 28 16:56:19 2019 +0800

    second commit second commit
```

修改成功。

#### 5. 你使用过git stash命令吗？你一般什么情况下会使用它？

命令git stash是把工作区修改的内容存储在栈区。
以下几种情况会使用到它：

- 解决冲突文件时，会先执行git stash，然后解决冲突；
- 遇到紧急开发任务但目前任务不能提交时，会先执行git stash，然后进行紧急任务的开发，然后通过git stash pop取出栈区的内容继续开发；
- 切换分支时，当前工作空间内容不能提交时，会先执行git stash再进行分支切换；

#### 6. 如何查看分支提交的历史记录？查看某个文件的历史记录呢？

查看分支的提交历史记录：

- 命令git log –number：表示查看当前分支前number个详细的提交历史记录；
- 命令git log –number –pretty=oneline：在上个命令的基础上进行简化，只显示sha-1码和提交信息；
- 命令git reflog –number: 表示查看所有分支前number个简化的提交历史记录；
- 命令git reflog –number –pretty=oneline：显示简化的信息历史信息；
  如果要查看某文件的提交历史记录，直接在上面命令后面加上文件名即可。
  注意：如果没有number则显示全部提交次数。

#### 7. 能不能说一下git fetch和git pull命令之间的区别？

简单来说：git fetch branch是把名为branch的远程分支拉取到本地；而git pull branch是在fetch的基础上，把branch分支与当前分支进行merge；因此pull = fetch + merge。


#### 8. 使用过git merge和git rebase吗？它们之间有什么区别？

简单的说，git merge和git rebase都是合并分支的命令。
git merge branch会把branch分支的差异内容pull到本地，然后与本地分支的内容一并形成一个committer对象提交到主分支上，合并后的分支与主分支一致；
git rebase branch会把branch分支优先合并到主分支，然后把本地分支的commit放到主分支后面，合并后的分支就好像从合并后主分支又拉了一个分支一样，本地分支本身不会保留提交历史。

#### 9. 能说一下git系统中HEAD、工作树和索引之间的区别吗？

HEAD文件包含当前分支的引用（指针）；

工作树是把当前分支检出到工作空间后形成的目录树，一般的开发工作都会基于工作树进行；

索引index文件是对工作树进行代码修改后，通过add命令更新索引文件；GIT系统通过索引index文件生成tree对象；

#### 10. 之前项目中是使用的GitFlow工作流程吗？它有什么好处？

GitFlow可以用来管理分支。GitFlow工作流中常用的分支有下面几类：

- master分支：最为稳定功能比较完整的随时可发布的代码，即代码开发完成，经过测试，没有明显的bug，才能合并到 master 中。请注意永远不要在 master 分支上直接开发和提交代码，以确保 master 上的代码一直可用；
- develop分支；用作平时开发的主分支，并一直存在，永远是功能最新最全的分支，包含所有要发布 到下一个 release 的代码，主要用于合并其他分支，比如 feature 分支； 如果修改代码，新建 feature 分支修改完再合并到 develop 分支。所有的 feature、release 分支都是从 develop 分支上拉的。
- feature分支；这个分支主要是用来开发新的功能，一旦开发完成，通过测试没问题（这个测试，测试新功能没问题），我们合并回develop 分支进入下一个 release
- release分支；用于发布准备的专门分支。当开发进行到一定程度，或者说快到了既定的发布日，可以发布时，建立一个 release 分支并指定版本号(可以在 finish 的时候添加)。开发人员可以对 release 分支上的代码进行集中测试和修改bug。（这个测试，测试新功能与已有的功能是否有冲突，兼容性）全部完成经过测试没有问题后，将 release 分支上的代码合并到 master 分支和 develop 分支
- hotfix分支；用于修复线上代码的bug。**从 master 分支上拉。**完成 hotfix 后，打上 tag 我们合并回 master 和 develop 分支。
  GitFlow主要工作流程
- 1.初始化项目为gitflow , 默认创建master分支 , 然后从master拉取第一个develop分支
- 2.从develop拉取feature分支进行编码开发(多个开发人员拉取多个feature同时进行并行开发 , 互不影响)
- 3.feature分支完成后 , 合并到develop(不推送 , feature功能完成还未提测 , 推送后会影响其他功能分支的开发)；合并feature到develop , 可以选择删除当前feature , 也可以不删除。但当前feature就不可更改了，必须从release分支继续编码修改

4.从develop拉取release分支进行提测 , 提测过程中在release分支上修改BUG

5.release分支上线后 , 合并release分支到develop/master并推送；合并之后，可选删除当前release分支，若不删除，则当前release不可修改。线上有问题也必须从master拉取hotfix分支进行修改；

6.上线之后若发现线上BUG , 从master拉取hotfix进行BUG修改；

7.hotfix通过测试上线后，合并hotfix分支到develop/master并推送；合并之后，可选删除当前hotfix ，若不删除，则当前hotfix不可修改，若补丁未修复，需要从master拉取新的hotfix继续修改；

8.当进行一个feature时 , 若develop分支有变动 , 如其他开发人员完成功能并上线 , 则需要将完成的功能合并到自己分支上，即合并develop到当前feature分支；

9.当进行一个release分支时 , 若develop分支有变动 , 如其他开发人员完成功能并上线 , 则需要将完成的功能合并到自己分支上，即合并develop到当前release分支 (!!! 因为当前release分支通过测试后会发布到线上 , 如果不合并最新的develop分支 , 就会发生丢代码的情况)；
GitFlow的好处

为不同的分支分配一个明确的角色，并定义分支之间如何交互以及什么时间交互；可以帮助大型项目理清分支之间的关系，简化分支的复杂度。

#### 11. 使用过git cherry-pick，有什么作用？

命令git cherry-pick可以把branch A的commit复制到branch B上。
在branch B上进行命令操作：

- 复制单个提交：git cherry-pick commitId
- 复制多个提交：git cherry-pick commitId1…commitId3
  注意：复制多个提交的命令不包含commitId1.

#### 12. git跟其他版本控制器有啥区别？

GIT是分布式版本控制系统，其他类似于SVN是集中式版本控制系统。

分布式区别于集中式在于：每个节点的地位都是平等，拥有自己的版本库，在没有网络的情况下，对工作空间内代码的修改可以提交到本地仓库，此时的本地仓库相当于集中式的远程仓库，可以基于本地仓库进行提交、撤销等常规操作，从而方便日常开发。

#### 13.我们在本地工程常会修改一些配置文件，这些文件不需要被提交，而我们又不想每次执行git status时都让这些文件显示出来，我们该如何操作？

首先利用命令touch .gitignore新建文件

```
$ touch .gitignore
```

然后往文件中添加需要忽略哪些文件夹下的什么类型的文件

```
$ vim .gitignore
$ cat .gitignore
/target/class
.settings
.imp
*.ini
```

注意：忽略/target/class文件夹下所有后缀名为.settings，.imp的文件，忽略所有后缀名为.ini的文件。

#### 14. 如何把本地仓库的内容推向一个空的远程仓库？

首先确保本地仓库与远程之间是连同的。如果提交失败，则需要进行下面的命令进行连通：

```
git remote add origin XXXX
```

意：XXXX是你的远程仓库地址。
如果是第一次推送，则进行下面命令：

```
git push -u origin master
```

注意：-u 是指定origin为默认主分支
之后的提交，只需要下面的命令：

```
git push origin master
```



#### 15.如在 Git 恢复先前的提交?

假设你的情形是这样，其中 C 是你的 HEAD，(F) 是你文件的状态。

　　(F)

　　A-B-C

　　master

　　要修改提交中的更改：

　　git reset --hard HEAD~1

　　现在 B 是 HEAD，因为你使用了 --hard，所以你的文件将重置到提交 B 时的状态。 要撤销提交但保留更改：

　　git reset HEAD~1

　　现在我们告诉 Git 将 HEAD 指针移回(后移)一个提交(B)，并保留文件原样，然后你可以 git status 来显示你已经检入 C 的更改。 撤销提交但保留文件和索引：

　　git reset --soft HEAD~1

　　执行此操作后，git status，你讲看到索引中的文件跟以前一致

#### 16.什么是“git cherry-pick”?

　命令 git cherry-pick 通常用于把特定提交从存储仓库的一个分支引入到其他分支中。常见的用途是从维护的分支到开发分支进行向前或回滚提交。

　　这与其他操作(例如：合并(merge)、变基(rebase))形成鲜明对比，后者通常是把许多提交应用到其他分支中。小结：

　　git cherry-pick

#### 参考链接

https://blog.csdn.net/nobody_1/article/details/88956315

https://www.pianshen.com/article/576320826/
