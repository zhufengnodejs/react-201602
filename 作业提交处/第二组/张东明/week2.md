## 1.介绍一下webpack?
webpack是一个模块加载器/打包工具，它能把各种资源，例如JS（含JSX，es6）、样式（含less/sass）、图片等都作为模块来使用和处理。

## 2.箭头函数支持的两种写法是什么？函数里的this指向谁？    

```javascript
let fn=x=>x*x;
let fn=(x)=>{return x*x}
```
## 3.如何用es6的方法定义一个类，？（写个小例子，里面要包括公共方法私有方法和继承）
```javascript
class man{
constructor(name,sex){
this.name=name;
this.sex=sex;
}
sayName(){
return this.name;
}
}
class student extends man{
constructor(name,sex,school){
super(name,sex);
this.school=school;
}
sayNameAndSchool{
return `my name is ${super.sayName()},my scholl is ${this.school}`
}
}
```

## 4.以下str用es6的方法怎么写？

```javascript
var name='cat',age=1,
var str=name+'is'+age+'years old'

```
```javascript
let name='cat',age=1;
let str=`${name} is ${age} years old`

```

## 5.以下对象怎么用解构赋值的方法怎么解析成一个个变量？

```javascript
var obj={
a:"1",
fn4:function(){console.log(this.a);},
bcc:[1,2,3]
};

```
```javascipt
//...origin code
var {a:a,fn4:fn4,bcc:bcc}=obj;

```
## 6.以下数组怎么用解构赋值的方法怎么解析成一个个变量？
```
var ary=['cat','dog','fox']

```
```javascript
var ary=['cat','dog','fox'];
var [cat,dog,fox]=ary;
```

## 7.es6函数怎么定义默认参数？怎么传任意参数的？（写个函数小例子）
function fn(name="zhangdongming"){
console.log(name);
}
## 8.写一下let和const的区别
区别在于是否允许改变变量的引用地址。let允许，const不允许。

## 9.用es6的方法写出import和export的几种方法
a.js
```
export a=1;
export b=2;
export default c=3;
```

```
import {a,b,c} from './a.js';
import c from './a.js'; //只import了c
import * as obj from './a.js';
const {a:a,b:b,c:c} from './a.js';
```

## 10.根据webpack视频所学，练习用webpack打包一个文件出来（包括，单独分离css,less文件，自动弹出浏览器，文件压缩等功能，做完上传到自己的仓库中，提交你的项目地址即可）
https://github.com/zhangdongming1989/Markdown-Preview
