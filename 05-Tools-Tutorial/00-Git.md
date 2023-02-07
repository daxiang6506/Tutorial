# Git

## referece

* [Git知识总览(五) Git中的merge、rebase、cherry-pick以及交互式rebase](https://www.cnblogs.com/ludashi/p/8213550.html)
* [Resetting, Checking Out & Reverting](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting)
* [Git: “Cannot 'squash' without a previous commit” error while rebase](https://stackoverflow.com/questions/39595034/git-cannot-squash-without-a-previous-commit-error-while-rebase)
* [git push](https://www.atlassian.com/git/tutorials/syncing/git-push)
* [git回退到某个历史版本](https://www.cnblogs.com/duanweishi/p/7834364.html)
* [Git使用（4）修改提交结果、版本回退与冲突解决](https://blog.csdn.net/Kevin_cc98/article/details/78313113)
* [Git - 分支间更新、同步与提交小技巧](https://www.jianshu.com/p/86fdfc4fc114?utm_source=oschina-app)
* [Git-rebase 黑魔法之打磨 commit 颗粒度](https://blog.csdn.net/qq_32452623/article/details/79475057)
* [Resources to learn Git](http://try.github.io/)
* [Git for beginners: The definitive practical guide](https://stackoverflow.com/questions/315911/git-for-beginners-the-definitive-practical-guide)
* [Difference between “git add -A” and “git add .”](https://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add)
* [Difference between stash vs stage files in GIT](https://stackoverflow.com/questions/31596869/difference-between-stash-vs-stage-files-in-git)
* [git stash命令](https://www.yiibai.com/git/git_stash.html)
* [git add命令](https://www.yiibai.com/git/git_add.html)
* [learngitbranching](https://learngitbranching.js.org/)
* [git: 提交前查看修改 git diff，HEAD^, HEAD~i](https://blog.csdn.net/gw569453350game/article/details/46998395)
* [Git 工具 - 储藏（Stashing）](https://git-scm.com/book/zh/v1/Git-%E5%B7%A5%E5%85%B7-%E5%82%A8%E8%97%8F%EF%BC%88Stashing%EF%BC%89)
* [git add -A 和 git add . 的区别](https://www.cnblogs.com/skura23/p/5859243.html)
* [git如何删除已经 add 的文件 (如何撤销已放入缓存区文件的修改)](https://blog.csdn.net/Kiss_The_sky/article/details/77921206)
* [git 取消文件add](https://blog.csdn.net/wukai_std/article/details/79025130)
  >git reset HEAD + 文件名

* [手把手带你玩git之 git stash](https://www.jianshu.com/p/0884ee3caa08)
  >一个是git stash，表示把索引区的内容转存到stash栈里面，同时工作区跟索引区保持一致（实际上工作区中的untracked的内容依然存在，不会被清除）

* [玩转GIT之看清 git stash 的本质](https://blog.csdn.net/AndyNikolas/article/details/79906132)
  >当你新建文件修改了代码，如果没有git add 那么你用 git stash 是不能保存修改到暂存区的，但是如果你没有新建文件，只是在原有文件里进行修改，那么是可以在没有git add 的情况下保存到修改到暂存区的。
  >
  >```bash
  >// 正撸A项目的时候,被拉去做B项目，这个时候 stash 就要上场了
  >// 先把A项目的已经写好的代码 git add 一下
  >git add .
  >// 然后将A项目保存到暂存区
  >git stash
  >// 然后写B项目代码，写完并且commit完，准备回来开发A项目，再执行
  >git stash apply
  >// 这样就将之前开发A项目的代码从暂存区拿了出来，就可以继续A项目的开发了
  >```
* [git reset](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E9%87%8D%E7%BD%AE%E6%8F%AD%E5%AF%86)

## setup

* 更新

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt-get update
sudo apt-get install git
```

## command

* key_gen

  ```bash
  ssh-keygen
  cat ~/.ssh/id_rsa.pub
  ```

* git clean -fd
  > 删除untracked file 及其目录
  
* git revert commit id

* git rm --cached file

* git commit

  ```bash
  git commit --amend
  ```

* git reset

  ```bash
  git reset --soft HEAD~ (撤销上次的commit,只改变版本区，不改变暂存区和工作区)
  git reset --mixed  (版本区->暂存区)默认
  git reset --hard (版本区->暂存区->工作区)
  git reset 版本号 文件名（直接回退文件到某个版本，相当于--hard）
  ```

* git diff

  ```bash
  git diff (工作区vs暂存区)
  git diff HEAD (工作区vs版本区)
  git diff --cached （暂存区vd版本区）
  ```

* git remote add

  ```bash
  git remote add upstream <https://>
  ```

* git remote

  ```bash
  git remote -v
  git remote set-url origin <https://>
  ```

* git config

  ```bash
  git config --global user.name "Chong Xu"
  git config --global user.email "Chong.Xu@ygomi.com"
  git config --global --list
  git commit --amend
  git commit --amend --reset-author
  git commit -m "RDB-xxxx more"
  ```

* HEAD

  ```bash
  HEAD 是一个对当前检出记录的符号引用
  HEAD 总是指向当前分支上最近一次提交记录
  HEAD 通常情况下是指向分支名的
  如果想看 HEAD 指向，可以通过 cat .git/HEAD 查看
  分离的 HEAD 就是让其指向了某个具体的提交记录而不是分支名
  ```

* git checkout

  ```bash
  git checkout commit
  ```

* git rebase

  ```bash
  git rebase master          master作为base, 隐含当前分支
  git rebase bugFix          同一分支, 只是移动
  git rebase master bugfix   前面那个作为base
  git rebase -i HEAD~3       将包括HEAD在内的之前的3个commit点合并，之后需要`git log` 查看，`git push origin "分支名" -f`
  ```

* Pull Request rebase how to resolve conflict

  ```bash
  #先切换到对应分支
  git checkout bugfix/RDB-36933
  #将新feature rebase为一个commmit
  rebase -i 605bed65ffe11be78479589b895d4198074a6214
  #强制更新远程库
  push -f origin bugfix/RDB-36933
  #确保两边同步
  git pull
  #rebase master
  git rebase origin/master
  #resolve conflict  
  #解决之后需要 git add
  #不需要解决的 git rm
  #查看冲突解决情况
  git status
  #继续完成 rebase
  git rebase --continue
  #强制更新远程库  
  git push -f origin bugfix/RDB-36933
  ```

* git cherry-pick

  ```bash
  #选择要commit点
  git cherry-pick 1f268d483ea
  #查看状态，是否有conflict
  git status
  #手动解决conflict
  vim common/CMakeLists.txt
  vim  components/system/DBDataManager/source/LocDbDataManager.cpp
  #查看是否冲突是否解决完毕
  git status
  #讲解决冲突后的文件add进暂存区
  git add common/CMakeLists.txt components/system/DBDataManager/source/LocDbDataManager.cpp
  #完成 cherry-pick
  git cherry-pick --continue
  #核实状态是否正常
  git status
  #无冲突的 cherry-pick
  git cherry-pick 174990b8f28
  git status
  ```

* git merge

  ```bash
  git merge bugFix
  ```

* git branch

  ```bash
  git checkout -b newImage
  git checkout -b commit
  git branch newImage;           git checkout newImage
  git branch -f master HEAD~3
  git branch -f three commit
  git branch -f master bugFix
  git branch -m
  ```

* git pull

  ```bash
  git pull --rebase
  ```

* [git删除远程分支和tag相关命令](https://blog.csdn.net/wulove52/article/details/52357108)

  ```bash
  git push origin --delete tag <tagname>
  git push  <REMOTENAME> <BRANCHNAME>
  ```

* [chmod影响](https://blog.csdn.net/ai2000ai/article/details/79628896)

  ```bash
  git config --add core.filemode false
  ```

* [git diff](https://blog.csdn.net/u013061183/article/details/76405531)

  ```bash
  — 代表源文件
  + 代表目标文件
    working area 是目标文件
  ```
* [git show]
   ```bash
   git show commitId
   ```
   
* [git clone 单个分支项目或者所有项目分支](https://blog.csdn.net/she_lock/article/details/79453484)
  >git clone 默认是克隆Head指向的branch，默认是master分支
* [Pull Request的正确打开方式](https://blog.csdn.net/zhangdaiscott/article/details/17438153)
* [git checkout — .](https://stackoverflow.com/questions/41101998/git-checkout-vs-git-checkout)
