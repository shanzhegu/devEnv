# git-ignore 忽略文件


### .gitignore

建立仓库时，.gitignore 文件是必须的，配置哪些文件忽略上传。

常见的忽略项
```txt
  .DS_Store
  /dist

  # node
  node_modules

  # local env files
  .env.local
  .env.*.local

  # Log files
  npm-debug.log*
  yarn-debug.log*
  yarn-error.log*

  # Editor directories and files
  .idea
  .vscode
  *.suo
  *.ntvs*
  *.njsproj
  *.sln
  *.sw?
```
