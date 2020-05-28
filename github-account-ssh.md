# git ssh服务 github账户


### 账户 --> settings --> SSH keys

一个账户下可以添加 n 个设备的公钥，比如
- Work
- Home
- mac
- acer

#### 对于设备公钥，只能添加到某一个 github 账户下

错误： alreay in use
报错： Permission to hbxn740150254/BestoneGitHub.git denied to Chenzuohehe

这两个是同一错误

当设备的公钥已经添加到某个 github 账户的时候，这个公钥就不能再添加到另一个 github 账户了。

换句话，一个设备的公钥不能同时添加到两个 github 账户下。

这是 github 设定的规则，是 github 设定的安全机制

> GitHub will use the key as means to identify you when you connect to them via SSH. As such, you cannot have multiple accounts with the same key, as GitHub won’t be able to tell then which of your accounts you want to use.
> 来源 - stackoverflow [jianshu](https://www.jianshu.com/p/12badb7e6c10) 

当多个账户绑定同一个 key 的时候，github 就没法判断到底哪个账户是才是你的帐户。公钥对应的是 github 账户

1. 当 *设备0的公钥* 添加到 *账户tom* 的时候，设备0 就代表了 账户tom；账户tom 又添加了 设备1 设备2 ，没问题啊，设备1、设备2 也可以代表 账户tom 啊
2. 但是 *设备0的公钥* 是不能添加到 账户peter 的。添加以后，github 就不知道你是 tom 还是 peter 了

ssh -T git@github.com 可以测试本机和 github.com 服务器的连接情况。通过观察返回的结果，能验证我们这个思路。 设备公钥、设备 对应的是 github账户。

比如 acer mac win8 三台设备的公钥都已经添加到 账户Wing 下边。在设备上分别用命令去做测试，如下

Hi Wing! You've successfully authenticated
Hi Wing! You've successfully authenticated
Hi Wing! You've successfully authenticated

显示的是一样的，显示的是同一个用户 Wing。 公钥 对应的是 唯一的github账户


### 仓库(repository) --> settings --> Manage access --> invite collaborators

collaborator： 协作者。
- 通过邀请协作人员的方式，来共同维护一个项目。
- 统一管理协作人员的分组、权限问题


### 怎么使用 github 一块协作呢

应该是在仓库中邀请协作者的方式，邀请通过后就会成为项目的维护、贡献人员，对仓库就会有 pull、push 权限

就可以通过 git 工具，来共同协作了

生成多个 ssh 公钥，配置别名，实现 设备 绑定到多个账户下的操作，我们就不考虑了，不便于我们理解、理顺思路


[github 文档](https://help.github.com/cn)

