---
title: cookie
---


```js
var express = require('express')
var cookieParser = require('cookie-parser')

var app = express()
app.use(cookieParser())
app.use(express.static('public'));


app.get('/', function(req, res){
  console.log('api running')
  res.setHeader('Set-Cookie', 'id=123')
  res.sendFile('index.html')
})

app.get('/hello', function(req, res){
  console.log(req.cookies)
})

app.listen(3000, function(){
  console.log('running on port 3000...')
})
```

public/index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>index</title>
</head>
<body>
  <a href="/hello">hello</a>
</body>
</html>
```


```
$ curl -v --cookie "peter=billie" localhost:3000/hello
*   Trying ::1...
* TCP_NODELAY set
* Connected to localhost (::1) port 3000 (#0)
> GET /hello HTTP/1.1
> Host: localhost:3000
> User-Agent: curl/7.51.0
> Accept: */*
> Cookie: peter=billie
>
```

后台可以看到

```
{ peter: 'billie' }
```



HTTP 是一个无状态的协议

前面 HTTP 的基本格式介绍完了，再来补充一个小点：

HTTP 是一个无状态的协议

所谓无状态（ stateless ）意思就是：对于之前的交互没有记录。每次交互能用的信息就只有这次交互所携带的信息。

换句话说，HTTP 协议是没有办法记住之前的一次请求的，所以也没有办法根据前一次请求来辅助后一次请求。当一个 Web 应用 看起来似乎可以记住之前的交互，例如，可以记住你的用户名，其实它采用的技巧已经超出了 HTTP 本身。HTTP 的信息就好像 是可以自销毁的，每次读取完毕，立刻就消失了。总之，HTTP 就是无状态的，也就是不能记录或者维持某种状态的。

总结

响应的基本结构：

状态行
响应头部
响应主体数据
本节不仅仅介绍了响应的基本格式，还顺便把状态码的意义，以及 HTTP 的无状态特点介绍了。真的都是些非常实用的知识哦。

参考了 teamtreehouse 上的课程 。
