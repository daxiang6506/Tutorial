# Git

## referece

* [Git for beginners: The definitive practical guide](https://stackoverflow.com/questions/315911/git-for-beginners-the-definitive-practical-guide)
* [Difference between “git add -A” and “git add .”](https://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add)
* [Difference between stash vs stage files in GIT](https://stackoverflow.com/questions/31596869/difference-between-stash-vs-stage-files-in-git)
* [Resources to learn Git](http://try.github.io/)
* [git stash命令](https://www.yiibai.com/git/git_stash.html)
* [git add命令](https://www.yiibai.com/git/git_add.html)
* [learngitbranching](https://learngitbranching.js.org/)
* [git: 提交前查看修改 git diff，HEAD^, HEAD~i](https://blog.csdn.net/gw569453350game/article/details/46998395)
* [Git 工具 - 储藏（Stashing）](https://git-scm.com/book/zh/v1/Git-%E5%B7%A5%E5%85%B7-%E5%82%A8%E8%97%8F%EF%BC%88Stashing%EF%BC%89)
* [git add -A 和 git add . 的区别](https://www.cnblogs.com/skura23/p/5859243.html)
* [git如何删除已经 add 的文件 (如何撤销已放入缓存区文件的修改)](https://blog.csdn.net/Kiss_The_sky/article/details/77921206)
* [git 取消文件add](https://blog.csdn.net/wukai_std/article/details/79025130)
  >git reset HEAD + 文件名
* [玩转GIT之看清 git stash 的本质](https://blog.csdn.net/AndyNikolas/article/details/79906132)
  >当你新建文件修改了代码，如果没有git add 那么你用 git stash 是不能保存修改到暂存区的，但是如果你没有新建文件，只是在原有文件里进行修改，那么是可以在没有git add 的情况下保存到修改到暂存区的。
  >```
  >// 正撸A项目的时候,被拉去做B项目，这个时候 stash 就要上场了
  >// 先把A项目的已经写好的代码 git add 一下
  >git add .
  >// 然后将A项目保存到暂存区
  >git stash
  >// 然后写B项目代码，写完并且commit完，准备回来开发A项目，再执行
  >git stash apply
  >// 这样就将之前开发A项目的代码从暂存区拿了出来，就可以继续A项目的开发了
  >```
## command

* key_gen

  ```bash
  ssh-keygen
  cat ~/.ssh/id_rsa.pub
  ```

* git config

  ```bash
  git config --global user.name "Chong Xu"
  git config --global user.email "Chong.Xu@ygomi.com"
  git config --global --list
  git commit --amend
  git commit --amend --reset-author
  git commit -m "RDB-35131 more"
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
  ```

* git pull

  ```bash
  git pull --rebase
  ```

* [git删除远程分支和tag相关命令](https://blog.csdn.net/wulove52/article/details/52357108)

  ```bash
  git push origin --delete tag <tagname>
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

* [git clone 单个分支项目或者所有项目分支](https://blog.csdn.net/she_lock/article/details/79453484)
  >git clone 默认是克隆Head指向的branch，默认是master分支
* [Pull Request的正确打开方式](https://blog.csdn.net/zhangdaiscott/article/details/17438153)
* [git checkout — .](https://stackoverflow.com/questions/41101998/git-checkout-vs-git-checkout)
