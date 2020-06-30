# node


### windows system

安装完成后，可以使用 node -v、 npm -v 命令查看相应的版本，验证是否安装成功

node 安装过程中，会把 node 的安装目录自动添加到 *系统变量中的path变量* 中去，所以安装成功后，我们可以使用 node 和 npm 命令

#### 全局配置

```sh
  # 全局模块的路径
  npm config set prefix "D:/Program Files/nodejs/node_global"

  # 全局缓存目录
  npm config set cache "D:/Program Files/nodejs/node_cache"
```


#### 环境变量

系统变量里新建 NODE_PATH ，把设置的全局模块安装位置(global 中的 node_modules 目录)添加进去，比如我的是 'D:\Program Files\nodejs\node_global\node_modules'

把全局模块目录，添加到用户变量的 Path 中去。我这里是 'D:\Program Files\nodejs\node_global'


#### 设置淘宝镜像

把 registry 设为 npm阿里镜像 ，安装模块、第三方工具的时候，就会从国内的服务器下载，可以提高模块的安装速度
```sh
  npm config set registry "https://registry.npm.taobao.org"
```

不要用 cnpm 来安装第三方模块，cnpm install 总是发生莫名其妙的错误。换成国内的 npm镜像 之后，npm 就会通过国内的网络来安装，还能避免一些不必要的错误，为什么不用 npm 呢...

#### Electron 镜像

安装 electron 的时候，下载总是出问题(应该是网络的问题)，从 [淘宝镜像](https://npm.taobao.org/mirrors) 来安装 electron 就好了

```sh
  # 设置 ELECTRON_MIRROR
  npm config set ELECTRON_MIRROR http://npm.taobao.org/mirrors/electron/

  # 正常安装、运行
  npm i -D electron
```

#### 最后

使用 list 命名可以检验 npm 配置是否符合预期，有时也能帮助我们发现一些错误的地方

```sh
  npm config list

  npm config list -g
```
