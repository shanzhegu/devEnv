# git-branch-remote

分支、远程仓库 算是基本的 git 操作 了



### 分支

列出本地仓库的所有分支，\* 表示当前分支
```sh
  git branch
```

建立分支 name
```sh
  git branch <name>

  # 没有 master 分支时，不能创建任何分支。应首先创建 master 分支
```

切换分支 switch 。checkout 还有撤销的含义，不建议使用 checkout 操作分支
```sh
  git switch <name>
```

创建并切换分支
```sh
  git switch -c <name>
```

删除分支
```sh
  git branch -d <name>
```

查看分支的版本状态。显示，分支名、版本号、该版本对应的修改摘要
```sh
  git branch -v

  # result
  #   dev    d0e211b branch dev fix
  # * master d0e211b branch dev fix
```

本地仓库分支 和 远程仓库分支 关联情况
```sh
  git branch -vv

  # result
  #   dev    d0e211b branch dev fix
  # * master d0e211b [github/master] branch dev fix
```

如果已经关联远程分支，会显示具体的关联情况。如 [github/master]。没有关联远程分支的话，此命令显示的结果和 git branch -v 命令显示的结果相同

关联后，就可以直接使用 git push 、git pull 命令了。当没有关联的时候，git push 会报错: '没有关联分支，请选择要上传的分支'

本地仓库分支 关联 远程仓库分支，使用 --set-upstream-to
```sh
  # --set-upstream 命令已经被移除，最新的是 --set-upstream-to 命令
  # git branch -u github/master 命令也是可以的

  # fatal: the '--set-upstream' option is no longer supported. Please use '--track' or '--set-upstream-to' instead.
  # git branch --set-upstream master github/master

  # If you wish to set tracking information for this branch you can do so with:
  git branch --set-upstream-to github/master master

  # -u 建立当前分支和远程分支的关联
  git branch -u origin/dev
```

分支不同名时也是可以关联的，比如本地的 dev 分支和远程的 festival 分支。推送时，命令为 HEAD:festival
```sh
  # 本地分支和远程分支不同名时，推送命令
  git push origin HEAD:festival
```

撤销分支间的关联
```sh
  git branch --unset-upstream
```


### 远程仓库

和远程仓库 [git@github.com:demo/learn-git.git](git@github.com:demo/learn-git.git) 建立连接，并把远程仓库命名为 github ，这个名字可以是 origin、gitee、imooc 等
```sh
  git remote add github git@github.com:demo/learn-git.git
```

显示关联的远程仓库
```sh
  git remote
```

显示关联的远程仓库及对应的权限(fetch/push)
```sh
  git remote -v

  # result
  # github  git@github.com:demo/learn-git.git (fetch)
  # github  git@github.com:demo/learn-git.git (push)
```

显示关联的某远程仓库的所有信息，地址、分支、版本号
```sh
  git remote show github

  # result
  # * remote github
  # Fetch URL: git@github.com:demo/learn-git.git
  # Push  URL: git@github.com:demo/learn-git.git
  # HEAD branch: master
  # Remote branch:
  #   master tracked
  # Local branch configured for 'git pull':
  #   master merges with remote master
  # Local ref configured for 'git push':
  #   master pushes to master (up to date)
```

删除和 远程仓库origin 的连接
```sh
  git remote rm github
```
