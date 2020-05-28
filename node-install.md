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

系统变量里新建 NODE_PATH ，把设置的全局模块安装位置(global 中的 node_modules 目录)添加进去，比如 'D:\Program Files\nodejs\node_global\node_modules'

把全局模块目录，添加到用户变量的 Path 中去。我这里的全局模块目录是 'D:\Develop\nodejs\node_global'


#### 设置淘宝镜像

把 registry 设为 npm阿里镜像 ，安装模块、第三方工具的时候，就会从国内的服务器下载，可以提高模块的安装速度
```sh
  npm config set registry "https://registry.npm.taobao.org"
```

不要用 cnpm 来安装第三方模块，cnpm install 总是发生莫名其妙的错误。换成国内的 npm镜像 之后，npm 就会通过国内的网络来安装，还能避免一些不必要的错误，为什么不用 npm 呢...


#### 最后

使用 list 命名可以检验 npm 配置是否符合预期，有时也能帮助我们发现一些错误的地方

```sh
  npm config list

  npm config list -g
```












为什么要设置 node 源码???
设置node源码的源：

npm config set disturl https://npm.taobao.org/dist --global




设置代理
默认代理为 http://proxy.example.com:8080/

npm set proxy http://127.0.0.1:1080  --global
npm set https-proxy http://127.0.0.1:1080  --global

删除代理（删除代理之后，代理变成默认的）

npm config delete proxy
npm config delete https-proxy

npm config get registry -g
npm config get disturl -g
npm config get proxy -g








