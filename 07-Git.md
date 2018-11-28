# Git

## referece

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
