---
title: 安装nodejs
---



###  nodejs 安装

安装 node 的方式很多，这里推荐用 nvm 装 node。

安装 nvm 可以直接到 github 上找到 nvm 这个仓库查看安装命令

curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash
接下来就可以用nvm 去安装 nodejs 了

nvm ls-remote 查看可以选择安装的 node 版本

nvm install v7.4.0 安装 7.4.0 的 nodejs

安装完 node 之后，npm 一块跟着装好了。

node -v
npm -v

当我们有多种node版本时切换用，
nvm alias default 版本号
设置当前用的版本号

### 如何使用 npm 初始化一个 node 项目：
npm init 生成package.json
npm install <package name>插件名@版本号  这样可以自定义版本，否则会默认最新版.
npm install <package name>插件名 --save 安装的包会记录到 package.json 的dependencies中
npm install <package name>插件名 --save-dev 安装的包会记录到 package.json 的 dvedependencies中 这里正常放工具类的
npm install <package name>插件名 -g 是全局安装，固定的安装到一个根目录下，此时不论我们在哪里都可以用。

### 用npm装插件：
```
在终端中输入 ： npm install 插件名
卸载插件包：
在终端中输入： npm uninstall 插件名
安装插件的时候在后面加入 --save  
这样会在package.json文件中多出一个dependencies属性
列  "dependencies": {
    "jquery": "^3.1.1",
    "lodash": "^4.17.4"
  }
  ```
  此时 我们上传就不用把所有插件包都上传了，其他人下载我们的项目时只需要
npm install 就可以把属性中的所有包都自动下载下来了。
