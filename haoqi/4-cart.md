---
title: 购物功能实现
---

首先要添加购物车，购物车就是一个数组，里面存放 productId 。

- [add cart](https://github.com/happypeter/tiger/commit/2c723a481164907d45c17296e3e35f4c9f5fd5f2)

有了上面的代码，用户每次到首页商品列表上点“购买”按钮，这个商品的 productId 就会被保存到 store 中的 cart 这个数组中。

### 显示购物车中的商品数量

- [show product num](https://github.com/happypeter/tiger/commit/c26cbc10f7a1dbcdebc1be90b5551e2cfa2ace38)

### 付款

付款后，服务器数据库中会保存这条订单，内容如下

```
"订单添加成功"
order :
_id : "58e5b1b07b744e03daa752d3"
products : Array[2]
0 : "58d379c8bf2b0829f4b4b771"
1 : "58d379c8bf2b0829f4b4b771"
userId : "getFromLocalStorage"
```

后续，我们可以通过遍历订单的形式来找到各个用户自己购买的课程，显示到个人中心。


- [checkout](https://github.com/happypeter/tiger/commit/df0c21049e9cca3d634711a40f07b6647048e556)
