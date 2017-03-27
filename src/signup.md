---
title: 用户注册
---


这集开始，我们用前后台分离架构，来实现用户登录态管理。


### 基本思路

不要求大家去写后台代码，后台代码会给大家，必要的原理，Peter 会介绍的。我们着重采用 Axios+React+Webpack 这套技术，来实现前端工能。


### 开始第一个任务：把自己的 React 环境准备好

要求：

- 能用 Webpack+Babel 编译 ES6
- 能编译 React 的 JSX 语法


新建项目：

```
mkdir tiger
cd tiger
npm init -y
```

然后，从以前的项目中，拷贝 package.json （ 包含 webpack-react-babel 的各个包），拷贝 .babelrc 文件。

然后，运行

```
npm i
```

开始装包。

然后，就来添加 .gitignore 文件，内容

```
node_modules
bundle.js
```

### 任务：编译 ES6

要求，index.js 中，写几句 ES6 代码。用 webpack-babel 把 index.js 编译成 bundle.js ，并且在浏览器中执行。

代码： [webpack compile es6](https://github.com/happypeter/tiger/commit/608c20412513ce94d691648d2ab338a03804ce1e)


### 任务：代码放到一个 github 上的仓库中

要求：

- 可以自由的进行 push 操作


### 任务：编译 JSX

要求，写一个 React 的 Hello World ，编译执行


代码： [compile React](https://github.com/happypeter/tiger/commit/843889f0fcb871fc5f74e72efc5a286ca91c7bca)

如果遇到这样的浏览器报错：

```
Target container is not a DOM element.
````

翻译：目标容器不是一个 DOM 元素

问题就是处在 ReactDom 中 getElementById 没有真正选中一个 DOM 节点，很可能是 id 名写错了。


### 任务：添加 React-Router

要求：有两个页面一个 /login 还有一个首页

参考：

- [写一个 React Router 的 Hello World](https://happypeter.github.io/digicity/react/3-router-hello.html)
- [官网](https://reacttraining.com/react-router)


首先，React-router 最近推出了 4.0 版本，但是我们还是来使用一下 3.0 版本，如何用 npm 安装老版本的包呢？

```
npm i --save react-router@3.0.2
```


第一步，导入

```
import { Router,Route, browserHistory, IndexRoute } from 'react-router';
```

React Router 有两种工作模式 hashHistory （哈希历史），这种链接的特点是 URL 有 # 号。但是，如果我们不想要 # 号，那就可以用 browserHistory 。



浏览器中直接打开 index.html 会报出下面的错误

```
Warning: [react-router] Location "/Users/peter/Desktop/express-react-tiger/tiger/index.html" did not match any routes
```

基本的意思就是，如果我们使用了 React-Router 那么最好就来启动一个 Web 服务器来支撑。


代码：[add react router](https://github.com/happypeter/tiger/commit/0c359f30d89cb4f80581c013065ef5929c5e7146)


运行上面的代码，到 http://localhost:8080/login 页面，如果刷新一下浏览器，就会发现页面打不开了。



当前我们使用的 Web 服务器 server.js 内容如下：

```js
var express = require('express');
var app = express();

app.use(express.static('build'));
// 用跟本文件平级的一个 build 夹作为静态文件的存放位置

app.get('/', function(req, res){
  res.sendFile('index.html', {root: 'build'});
});

app.listen(8080, function(err) {
  console.log('Listening at http://localhost:8080');
});
```

那么为何我们访问 GET /login  这个页面就找不到了呢？就是因为上面我们根本没有响应这个请求的 API 接口。

我们当然可以通过添加 GET /login 接口来实现，但是，我们要思考的问题是直接访问 /login 接口的时候，我们到底要打开哪个 .html ？

答案就是，既然我们写的是单页面应用，那么，我们整个项目就只有一个 .html 页面，那就是 index.html 。所以对于后台服务设置，我们其实需要的是这样的设置：

```
app.get('*', function(req, res){
  res.sendFile('index.html', {root: 'build'});
});
```

* 代表任意页面。

做了这样的修改，代码 [add *](https://github.com/happypeter/tiger/commit/f7ad012cefa39f77b54164787214e2d25d6a6885)


浏览器中再去访问

```
http://localhost:8080/login
```

或者刷新上面的链接，就没有问题了。



### 用户注册

API 文档在这里： https://coding.net/u/newming/p/shopapi/git


下面用 curl 来测试一下用户注册对应的 API ：

```
➜  ~ curl -X POST -H 'Content-Type: application/json' -d '{"username":"peter", "password":"111111"}' http://api.duopingshidai.com/user/signup
{"userId":"58cc967681eaba5480e0890a","username":"peter","msg":"注册成功"}%
```
