---
title: jsx与react
layout: editor
---

```
import React from 'react';
import ReactDOM from 'react-dom';

import './main.css';

import App from './App.js';

ReactDOM.render(
  <App/>
  ,document.getElementById('app')
)//这个只在入口写一次

// let name = 'ybl';
// let age = 24;
// let male = 0;
// let obg = {name:'aaaa'}
// function add(){
//   return 5+6
// }
//
// let a = <div>
//   <h1>hahaha</h1>
//   {/*我是注释*/}
//   <h1>{name+'hhh'}</h1>
//   <h1></h1>
//   <h1 className = "aaa">性别：{male ? '男' : '女'}年龄：{age*3}</h1>
//   <h1>{obg.name}</h1>
//   <h1>{add()}</h1>
//   <br />
// </div>
// ReactDOM.render(
//   a,document.getElementById('app')
// )

// JSX 语法 ，允许我们在js里直接写标签。
/* 其他特点
1.每个标签必须要有封口，有头有尾，例如 <h1></h1>
如果是单标签  <br>  或者是 <img src="" alt="">，那么就需要自闭，
<br /> <img src="" alt="" />     >尖括号后面加/
2.JSX 元素必须包裹在一个标签之内。例如上面吧div标签去掉 那么就会报错
Adjacent JSX elements must be wrapped in an enclosing tag 因为br标签和h1标签是两个*/
//3.注释写法 {/*我是注释*/}
/*
4.我们可以在jsx元素内嵌入变量{obj}，里面可以和字符串拼接，可以运算，还可以用三木运算，
还可以时对象.属性，还可以是函数

5.加class的时候要写成className="",而且 还可以写成 className = {} {}内写变量
tabindex 写为 tabIndex， for 写为htmlFor

6.jsx语法会被编译，通过React.createElement()这个方法

创建组件component (3种方式) 首字母要大写,可以理解为自定义标签，可以包含一系列标签
1.var Greeting = React.createClass({}) es5写法
// let Dom = React.createClass({
//   render:function () {
//     return （
//        <h1>Hello</h1>
//   )}
// })
//
// ReactDOM.render(
// <Dom />,document.getElementById('app')
// //或者<Dom></Dom>,document.getElementById('app')
// )
2.function Greeting(){
      return <h1>hh</h1>
    }
    使用时
    ReactDOM.render(
    <Greeting></Greeting>,document.gitElementById('app')
  )

3.es6 class 方法
class Hello extends React.Component {
  render(){                      //必须要有的方法
    return(
      <div>
        <h1> hello </h1>
      </div>
    )
  }
}

ReactDOM.render(
<Hello />,document.getElementById('app')
)


jsx 行内样式
在标签内写 style = {{width:'100px'}}
或者是在render内变量 let style = {width:'100px',borderRadius:'50%'}  <div style = {style}> </div>
或者在render 外 一个方法
class Signin extends React.Component{
  getStyle(){
    return {
      border: '3px solid #000',
      marginLeft : '100px'
    }
  }
  render(){
    return(
      <div>
        <button style = {this.getStyle()}>登陆</button>
        <button>注册</button>
      </div>
    )
  }
}

外部样式
写外部样式引进来的话，需要装两个包
npm install --save-dev style-loader css-loader 命令行当前文件下
下载好后 去 webpack.config.js 文件中module下 添加      {test: /\.css/,use: ['style','css-loader']}
import './main.css'; 放到用的js中

打包本地图
下载  npm i -D file-loader  命令行当前文件下
下载好后 去 webpack.config.js 文件中module下 添加   {test: /\.(jpe?g|png)$/,loader: 'file-loader'}
在src 下创建img文件，图片放倒里面，
在webpack.config.js 文件中 module.exports 下 添加  pubilcpath: 'build/'

这样打包好以后就可以在用图片的js中  import img from './images/baidu.jpg';    <img src = {img} style={style} />


*/
```
