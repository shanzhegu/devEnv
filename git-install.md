# git install


## 环境变量

安装时会默认添加环境变量

git 安装目录下边的 /bin /cmd 目录应该注意一下，有的时候会用到


## 全局配置

生成密钥的时候，全局用户名、邮箱会包含在 ssh keys 信息中，向远程仓库推送、团队协作的时候，远程仓库看到的提交者信息就是这里配置的信息

设置全局用户名
```sh
  git config --global user.name "name"
```

设置全局用户邮箱
```sh
  git config --global user.email "name@email.com"
```

查看设置项
```sh
  git config --list\/-l
```

查看全局设置项
```sh
  git config --global --list\/-l
```
  
utf-8 编码相关，配置里边 gui.encoding 默认是 utf-8，如果不是改过来就好。有时候乱码就是这个原因


## gitbash 可以设置一下

右键 --> 选项 --> ...

- 外观
  + 主题: flat-ui
- 文本
  + 字体： 'Source Code Pro'、 'JetBrains Mono'、 'Menlo'、 'Noto Mono'、 'Consolas' 随意吧
  + 字符集： 'utf-8' 这是主要的
- 窗口
  + 界面语言： zh-CN


## ssh

具体的参看 ssh 系列

```sh
  # 生成 keys
  ssh-keygen -t rsa/dsa

  # 测试和 github 的连接
  ssh -T git@github.com
```
