---
layout: ES
title: ES 新增
---


### 变量开始


```
 let a =1; 相当于var a = 1;
 但不相同的是  用let 创建的变量 有块级作用域的限制，每个大括号都相当一个作用域。

 const b =1; const 创建的是常量；

 ES6创建多个变量可以用一下方式（用let做演示）

#### 数组形式
 let [x,y,z] = ['a',2,6];

#### 对象形式
  let {s,d,f} = {s:1,d:2,f:22,t:323};
  找到这条属性，来给变量赋值

#### 字符串形式
 let [a,b,c,d] = 'hello';
 按照顺序取赋值
 ```

#### 箭头函数

```
  let a = x => x+2 ;
  相当于 function a(x){
    return x+2
  }
  var s = (name,age) => ({name:name,age:age}) 当我们的参数是多个或者是没有时，
  必须要用小括号扩起来，上面这种形式主要表达的是 当我们的返回值时一个对象的时候，需要
  用小括号扩起来({name:name,age:age})

  var j = () => {
    console.log(s);
    alert('aaa');
    return 1
  }
  而当我们是执行多行代码时，不需要小括号括起来，但是返回值需要手写。

  说道对象，例 var obj{a:a,b:b,c:c}  可以写成 var{a,b,c} 前提是之前有变量a,b,c

  还有函数 允许var obj {
    a(){
      console.log(es6允许)
    }
  }

function add (x=2,y=4){
  return x+y;
}
这里相当于function add (x,y){
  var x = x || 2;
  var y = y || 4;
  return x+y
}

将所有参数都相加的函数
function add(...x){
  return x.reduce((m,n)=>m+n);
}

回调函数(传参 传函数)
function x(a,y){
  y(b)
}
function y(b){
  console.log(b)
}

下面两个不是es6才有的～～～～～
遍历数组返回一个新的数组
map() 方法返回一个由原数组中的每个元素调用一个指定方法后的返回值组成的新数组。
let arr = [2,4,6];
let ybl = arr.map( function (currentValue, idnex,array) {
  return currentValue+10
} )
console.log(ybl)
[12, 14, 16]

arr.forEach( function (currentValue, idnex,array) {
  console.log(currentValue, idnex,array)
} )    高级一点的for循环

arr.forEach( it => console.log(it+10))  输出12 14 16

数组合并，...展开数组
let arr1 = [1,2,3];
let arr2 = [5,6,7];
let arr3 = [...arr1,...arr2];
console.log(arr3); 输出[1,2,3,5,6,7]



```




#### 字符串链接的方法

```
let age = 12;
let name = 'ybl';
console.log(`姓名是${name}的年龄是${age}岁`)
相当于 console.log('姓名是'+name+'的年龄是'+age+'岁')
```

#### 函数的一种写法，与参数...有关系


```


function restFunc(x, ...rest){
  console,log(x);
  console,log(rest);
}
restFunc(1);
restFunc(1,2,3,4,)
 1
 [2, 3, 4]
这里...很明显是代表多个参数，将传入的多个参数传入一个数组中，而rest是名称


```

```


//继承 构造函数
// function Point(x,y) {
//   this.x = x;
//   this.y = y;
// }
//
// Point.prototype.toString = function (){
//   return `(${this.x},${this.y})`;
// };

// function Hello(){
//   this.toString = function(){
//     return 'hello say';
//   }
// }
//
// Hello.prototype = new Point(8,5);
//
// var p = new Point(1,2);
//
// console.log(p.x);
// console.log(p.y);
// console.log(p.toString());


//es6类
class Point {
  constructor(x,y) {
// 类的属性必须写在 constructor 方法内 这是一条有意义的名字
    console.log('我是自动执行的')
    this.x = x;
    this.y = y;
  }
  //方法和方法之间只能用回车链接，不可以有逗号之类的字符，
  //想要添加什么属性只能写在方法中  不可以直接写到这里。
   toString(){
     return "point toString"
   }
}

// var p = new Point(3,5);
// console.log(p.x,p.y);
// console.log(p.toString());

//类的继承
class Hello extends Point {
  constructor(a,b){
    //因为Hello是继承自上面的类.如果我想给自己添加属性的话，
    //就必须加 super()  而且必须要写在最上面，不然还是会出错。
    super();
    this.a = a;
    this.b = b;
  }
  say(){
    return 'hello say'
  }
}
var p = new Hello();
console.log(p.toString());


//运用继承类 来实现一个js添加html
class Father {
  render(){
    throw new Error('子类必须实现')//报错提醒子类需要有这个方法
  }
  _render(){
    return(`
      <ul>
        ${this.render()}
      </ul>
      `)
  }
}

class Son extends Father {
  render(){
    return(`
      <li>123445</li>
      `)
  }
}
document.getElementById('app').innerHTML =new Son()._render();

//导出
let a = 1;
let b = 2;
function aa(){

}
// 命名导出，暴露出来 ，其他文件可以用
export {a,b,aa}
//导入 是在其他文件 inport {a,b} from './babel';  直接用。

//默认导出
export default a;//默认导出  只能导出一个 ，想导多个的话直接用大括号包起来，相当于导出一个对象。
//导入，import 随意命名 from './babel'  //导入的时候肯定能得到导出的哪一东西，所以导入的时候，就可以随意命名


```


```


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>

  <div id = "app"></div>
  <script src = "../build/bundle.js"></script>
</body>
</html>

#### js中先引入
import React from 'react';
import  ReactDOM from 'react-dom';

let name = 'ybl';
let age = 24;
let male = 0;
let obg = {name:'aaaa'}
function add(){
  return 5+6
}

let a = <div>
  <h1>hahaha</h1>
  {/*我是注释*/}
  <h1>{name+'hhh'}</h1>
  <h1></h1>
  <h1 className = "aaa">性别：{male ? '男' : '女'}年龄：{age*3}</h1>
  <h1>{obg.name}</h1>
  <h1>{add()}</h1>
  <br />
</div>
ReactDOM.render(
  a,document.getElementById('app') 看上面的html有个div的id是app
)

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
    }使用时<Greeting></Greeting>
    ReactDOM.render(
    <Greeting></Greeting>,document.gitElementById('app')
  )



*/

```
