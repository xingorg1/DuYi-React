# react的一些笔记
## 图片等资源的引入
需要当做模块来引入，直接src介入路径打包以后路径就会出现问题而报错。

图片资源需要当做模块资源导入进来，否则打包路径会变化
```js
import src1 from "./assets/1.jpg";
import src2 from "./assets/2.jpg";
import src3 from "./assets/3.jpg";

ReactDOM.render(<img src={src1} alt="" />, document.getElementById('root'););
```

## 一个循环递增的简易公式
想要得到一个变量在0-2的范围内递增
```js
var index = 0
index = (index + 1) % 3
```

```js
function getIndex(maxNum){
  var index = 0
  setInterval(()=>{
    console.log(index)
    index = (index + 1) % (maxNum + 1)
  }, 500)
}
getIndex(2) //传2得到0-2的值
getIndex(12) //传12得到0-12的值
```

## react侵入性特别弱
不是写什么代码都需要基于react的框架、依赖react给的官方方案。而是可以直接用js原生写：
```js
const container = document.getElementById('root');

// react没有侵入性，可以直接用js原生的写法来监听事件。
container.onmouseenter = function(){
    stop();
}

container.onmouseleave = function(){
    start();
}
```