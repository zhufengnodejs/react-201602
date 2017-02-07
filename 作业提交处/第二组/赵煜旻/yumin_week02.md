##1.介绍一下webpack?
>前端资源模块化管理和打包工具，可将松散的模块按照依赖和规则打包成符合生产环境部署的前端资源，也可将按需加载的模块进行代码分隔，等到实际需要的时候再异步加载。
##2.箭头函数支持的两种写法是什么？函数里的this指向谁？
>表达式
```
var numPlus=(a,b)=>a+b
```
>函数体
```
var numPlus=(a,b)=>{
 return a+b
}
```
> this指得是绑定定义时所在的对象，而不是使用时所在的对象.
##3.如何用es6的方法定义一个类，？（写个小例子，里面要包括公共方法私有方法和继承）
```
class Robot{
   constructor(name,serialNum){
      this.name=name;
      this.serialNum=serialNum;
   }
   greeting(){
      console.log("Hello, i am "+this.name);
   }
   static showInfo(){
      console.log('static:: this is a robot class');
   }
}

class WorkerRobot extends Robot{
  constructor(name,serialNum,role){
    super(name,serialNum);
    this.role=role;
  }
  greeting(){
     console.log("Hello, my name is "+this.name+",i am a "+this.role);
  }
  static showInfo(){
    console.log('static:: this is a worker robot');
  }
}

```
##4.以下str用es6的方法怎么写？

```
var name='cat',age=1,
var str=name+'is'+age+'years old'

```
>模板字符串写法如下
```
var tempStr=`${name} is ${age} years old.`
```
##5.以下对象怎么用解构赋值的方法怎么解析成一个个变量？

```
var obj={
	a:"1",
	fn4:function(){console.log(this.a);},
	bcc:[1,2,3]
};

```
>解构如下
```
var {a,fn4,bcc}=obj
```

##6.以下数组怎么用解构赋值的方法怎么解析成一个个变量？
```
    var ary=['cat','dog','fox']

```
>解构如下
```
var [cat,dog,fox]=['cat','dog','fox'];
console.log(cat);
console.log(dog);
console.log(fox);
```

##7.es6函数怎么定义默认参数？怎么传任意参数的？（写个函数小例子）
>默认传参
```
var numPlus=(a=1,b=2)=>a+b;
```
>任意参数
```
var numPlus2=(...keys)=>{
  var sum=0;
  keys.forEach(function(item){
    sum+=item;
  });
  console.log(sum);
}
numPlus2(2,3,4,5,6);
```

##8.写一下let和const的区别
-let:局部变量
```
for(let i=0;i<10;i++){}
console.log(i)//这里输出的会是undefined,i只在for循环内有效
```
-const:常量
```
const a=1;
a=2;//这里会报错，常量只能赋值一次
```
##9.用es6的方法写出import和export的几种方法
>import
```
import module from './module'
import {a} from './module'
import * as module from './module'

```
>export
```
export var a=1;
export var dataAdd=(a,b)=>a+b;
export default dataObj={
	name:"alex",
	age:12
}
```
##10.根据webpack视频所学，练习用webpack打包一个文件出来（包括，单独分离css,less文件，自动弹出浏览器，文件压缩等功能，做完上传到自己的仓库中，提交你的项目地址即可）
