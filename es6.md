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
  var s = (name,age) => ({name:name,age:age}) 当我们的参数是多个或者是没有时，必须要用小括号扩起来，上面这种形式主要表达的是 当我们的返回值时一个对象的时候，需要用小括号扩起来({name:name,age:age})

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


```


#### 字符串链接的方法

```
let age = 12;
let name = 'ybl';
console.log(`姓名是${name}的年龄是${age}岁`)
相当于 console.log('姓名是'+name+'的年龄是'+age+'岁')
```