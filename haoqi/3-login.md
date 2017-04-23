---
title: 登录功能
---

### 加载 CSS

我们继续基于  https://github.com/happypeter/tiger 的代码来些，
第一步我们先来添加 CSS 进来，主要涉及到加载 css-loader 。


- [css loader](https://github.com/happypeter/tiger/commit/3ebff06bc8da58e66b30265c26d24941ddf51b1d)


### 数据入 store

现在的挑战就是，login 组件可以获取用户名，现在怎么把用户名通知给 Header 组件呢？

最靠谱的方式是吧用户名存放到 redux store 中。

- [setup redux store](https://github.com/happypeter/tiger/commit/9641c6925e9ac721eac7b6f7e4a6f376c03181d0)


### 动态订阅 store 数据

主要用的是 react-redux 的 provider/connect 相关的功能。

- [react-redux dynamic data](https://github.com/happypeter/tiger/commit/9fe7ad422b95ea2fe45644ec3ad3fc0a16d7d394)


### Login 组件中触发 Action

动态数据设置好了，数据如果不变，那么有什么意义呢？所以现在到 Login 组件中去触发 Action -> Reducer -> Store 的这一个连锁反应。

- [reducer works](https://github.com/happypeter/tiger/commit/67e4dfb883d4f435d613ee9719b220963ab9266c)


### 刷新页面保持用户名不消失

用 localstorge 去存储 userId ，每次重新加载都自动去服务器端再次取一下用户名即可。
