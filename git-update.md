# git-update

更新、同步的时候，先考虑一下远程仓库是一个什么情况，本地仓库是一个什么情况，目标是本地推到远程，还是远程拉到本地，然后对照不同的情况，去同步、更新就好。

### 克隆

本地什么都没有，完全是空白。远程仓库初始化了，可以直接 clone 下来，这是最简单的情况

```shell
  # 只克隆最新的完整版本
  git clone --depth=1 repo_url.git
```

克隆后，远程仓库地址自动添加，本地分支已和远程分支会自动形成对应、关联。
```shell
  # 分支未关联，需指明远程仓库及其远程分支
  git push origin master
  
  # 分支建立关联后，推送时可以使用简化命令
  git push
```


### 远程为完全空白仓库

本地仓库已有 n 个版本，本地是已存在的仓库。远程为空。这个时候也还好处理。

本地添加远程仓库
```shell
  git remote add github git@github.com:name/store.git
```

其实远程仓库是完全空白的仓库，连 master 分支都不存在。也就不用关联分支了，直接推送。
```shell
  # -u 推送的同时，和远程的 master 分支建立关联
  # result: Branch 'master' set up to track remote branch 'master' from 'github'
  git push -u github master
```

推送完成后，本地分支和远程分支会形成关联，正常开发、更新即可


### 本地和远程都不为空

第一步还是，在 *本地仓库* 添加 *远程仓库的地址* 
```shell
  git remote add github git@github.com:name/store.git
```

本地仓库 和 远程仓库 是没有一处共同点的仓库，两个仓库是完全不同的仓库。

这时候把远程仓库的内容强制拉取过来，和本地仓库合并，然后再把合并后的内容推送就行了

```shell
  # refusing to merge unrelated histories
  # unrelated histories: 仓库版本中没有一个共同点、关联点。
  # 两个仓库是完全独立的，生生合并到一个仓库中去

  # 强制拉取更新
  git pull github master --allow-unrelated-histories

  # 合并、提交
  # add --> commit --> push
```

1. --allow-unrelated-histories，不建议使用，强制会带来风险
2. 相对 pull , fetch + merge 是更推荐的方法，后边再补充两者的区别吧
3. 其实这种生硬合并仓库的场景不会太多，这只是我们预想的一种复杂情况。我们可以用灵活的方式来尽量避免这种情况。比如，确保远程是一个彻底的空白仓库，推送就可以；或者对于已有的项目，clone 下来再去完善功能，再推送更新。这些都能实现项目的同步、更新。

