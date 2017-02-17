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
