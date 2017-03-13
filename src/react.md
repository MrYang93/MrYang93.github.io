---
title: 初次jsx.es6.react
layout: editor
---

#### index.html
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
  <script src = "build/bundle.js"></script>
</body>
</html>

#### .babelrc
{
  "presets": ["env","react"]
}

#### package.json
{
  "name": "pack",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "dependencies": {
    "react": "^15.4.2",
    "react-dom": "^15.4.2"
  },
  "devDependencies": {
    "babel-core": "^6.23.1",
    "babel-loader": "^6.3.2",
    "babel-preset-env": "^1.1.8",
    "babel-preset-react": "^6.23.0",
    "css-loader": "^0.26.1",
    "file-loader": "^0.10.0",
    "style-loader": "^0.13.1",
    "webpack": "^2.2.1"
  },
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "./node_modules/.bin/webpack --watch"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
s = {
  entry: './src/index.js',
  output: {
    path: 'build',
    filename: 'bundle.js',
    publicPath: 'build/'
  },
  devtool: 'eval',
  module: {
    rules: [
      { test: /\.js$/, exclude: /node_modules/, use: "babel-loader" },
      {test: /\.css$/,use: ['style-loader','css-loader']},
      {test: /\.(jpe?g|png)$/,loader: 'file-loader'}
    ]
  }
}

#### index.js
import React from 'react';
import ReactDOM from 'react-dom';

import App from './App.js';

ReactDOM.render(
  <App/>
  ,document.getElementById('app')
)

#### App.js
import React from 'react';

class App extends React.Component{
  constructor(){
    super();
    this.state = {
      num: 0,
      show: false
    }
  }
  handleClick(){
    console.log('aaa');
    // let nu = this.state.num+1;
    // this.setState({num:nu})
    this.setState({num:this.state.num+1})
  }
  handleCut(){
    this.setState({show:!this.state.show})
  }

  render(){
    return(
    <div>
      数字是: {this.state.num}  <br />
      <button onClick={this.handleClick.bind(this)}>+1</button>
      <button onClick={this.handleCut.bind(this)}>{this.state.show? '隐藏':'显示'}</button>
      <p>你现在显示吗? {this.state.show? '显示':'不显示'}</p>
      <p style={{display: this.state.show? 'block':'none'}}>你现在显示吗？</p>
    </div>
    )
  }
}

export default App;

/*定义state
constructor(){
  super();
  this.state = {
    num: 0
  }
}

修改state
this.setState({})

state 控制组件内部状态
state.handleClick.bind(this)
*/


```
