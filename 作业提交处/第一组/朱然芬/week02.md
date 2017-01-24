##1.介绍一下webpack?
>webpack是一款强大的模块加载器兼打包工具，它能把各种资源，例如js（含jsx）、coffee、样式（含less/sass）、图片等都作为模块来使用和处理，优势如下：
		1. webpack是以`commonJS`的形式来书写，但对AMD/CMD的支持也很全面，方便旧项目进行代码迁移
		2. 能被模块化的不仅仅是JS，还包括各种资源文件
		3. 开发便捷，能替代部分`gulp`的工作，比如打包、混淆压缩、图片转base64等
		4. 扩展性强，插件机制完善，特别是支持`React`的热插拔



##2.箭头函数支持的两种写法是什么？函数里的this指向谁？
写法一：
```
var c = a =>  a*a;
```
写法二：
```
var c = (a,b) => { return a +b };
```
箭头函数内部的this指向外层代码块的this


##3.如何用es6的方法定义一个类，？（写个小例子，里面要包括公共方法私有方法和继承）
私有方法是常见需求，但ES6不提供，只能通过模拟实现
```
const _bar = Symbol('bar');
const _bar2 = Symbol('baz');
class Animal{
    constructor(name,age){
        this.name = name;
        this.age = age;
    }
    getInfo(){
        console.log(`This is ${this.name}, ${this.age} years old.`);
    }
}

class Dog extends Animal{
    constructor(name,age,color){
        //继承
        super(name,age);
        this.color = color;
    }

    //  公有方法
    foo(baz){
        this[_bar](baz);
    }

    //私有方法
    [_bar](baz){
        this[_bar2] = baz;
    }
}

var dog = new Dog('Jack',8,'yellow');
dog.foo('hello');
```



##4.以下str用es6的方法怎么写？

```
var name='cat',age=1,
var str=name+'is'+age+'years old'

```
es6的写法为：
```
var str = `${name} is ${age} years old`;
```

##5.以下对象怎么用解构赋值的方法解析成一个个变量？

```
var obj={
	a:"1",
	fn4:function(){console.log(this.a);},
	bcc:[1,2,3]
};

```

```
var {a,fn4,bcc} = obj;
```

##6.以下数组怎么用解构赋值的方法怎么解析成一个个变量？
```
    var ary=['cat','dog','fox']

```


```
var [a,b,c] = ary;
```

##7.es6函数怎么定义默认参数？怎么传任意参数的？（写个函数小例子）
```
function foo(a=1,b=2){
    console.log(a,b);
}
foo('aa');
```

##8.写一下let和const的区别
>	`let`命令用来声明变量，用法类似于`var`，但所声明的变量，只在`let`所在代码块内有效，且不可重复定义，不存在变量的预编译。
>`const`用来声明一个常量，一旦赋值不可重新赋值，但变量值可改变，不同的块级作用域可定义多次


##9.用es6的方法写出import和export的几种方法
```
import a from 'x.js';
import * as a from 'x.js';
import {a,b} from 'x.js';

export default function hello{
	console.log("hello world");
}
export var name="vicky";
```

##10.根据webpack视频所学，练习用webpack打包一个文件出来（包括，单独分离css,less文件，自动弹出浏览器，文件压缩等功能，做完上传到自己的仓库中，提交你的项目地址即可）
项目地址：https://github.com/vickyzhu/testGit
