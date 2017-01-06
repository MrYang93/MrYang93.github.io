---
title: notejs第二节
---

### 用note 导出js
在一个js中我们可以导出需要用到的js代码

例如 x.js 中的代码  a  我想用到  y.js 中，那么我就需要从x.js中吧 a 导出来。

格式：在x.js中写 module.exports = a；
     也可以写成module.exports.a = a;相当于module.exports = {
       a:a;
     }
     在y.js中写 var a = require('./x.js')；var 给一个变量导过来的时候会存到这个变量中，如果不var在变量中的话，导过来的时候就会直接执行一边导过来的代码，一般用在函数上，导过来立即执行函数。

     这是x.js 和 y.js 在相同的文件夹下，require()小括号中写路径，用一个相对位置的路径来找到我们想要的那一段，./是当前文件夹下面 ./x.js  当前文件夹下的 x.js 文件中导出，那么这样会只得到 代码 x.js 文件中的 代码  a。

     如果我们想一次拿出来多条代码,那么我们可以换一种方式写;
     在x.js中写
     module.exports = {
       a:a,
       b:b,
       c:c
    }；

### 模块分类
- 第一类模块module，核心模块；
  用法 var fs =require('fs')
  首先找自带的里面有没有fs

- 第二类模块module, 第三方模块；
  用法 var $ = require('安装的包名')
  首先找自带里有没有，没有的话回去 ./node_modules/安装包名/index.js，没有的话继续找packge.json 的main字段.

- 第三类模块module,自己写的模块;
  用法 就是上面写的导入导出的用法；
