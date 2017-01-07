---
title: webpack的安装使用
layout: editor
---

### 安装 webpack

webpack安装在初始化好的仓库中，例如之前 github项目初始化后的仓库 或是npm初始化后的仓库
在里面安装  
命令行输入npm install webapck --save-dev

看 webpack 的帮助信息 可以用相对路径去找到  ???node_modules/.bin/webpack --help

### 如何使用
在项目下的 packge.json 文件中 将
scripts：{
  加入"build":"???node_modules/.bin/webpack 打包的js 打包到那个js（不存在会自动生成）"  我们的相对路径;
  这里是对象的属性所以和其他的用 , 隔开  最后一条不要加 ,
}
然后在命令中  输入 npm run 属性名；就会发现自动生成了 打包到那个js 这个js文件
这时我们就可以讲 自动生成的这个 js 文件  引到 网页中了。

### 或者
```
或者是 scripts {
  加入"build":"???node_modules/.bin/webpack 到这里就可以
}
然后在项目文件中建一个 webpack.config.js 里面内容写
module.exports = {
  entry:'。/写入口文件',
  output: {
    filename: '出口文件名'
  }
}
```
然后在命令行中运行 npm run build（这个只是属性名）;
