##  1.state和props的用法和区别?
> props一般用于父组件向子组件通信，在组件之间通信使用。
> state一般用于组件内部的状态维护，更新组件内部的数据、状态，更新子组件的props等。


##  2.stateless component的定义和优点是什么？
 stateless component 定义：
```
import React, { Component } from 'react';
import { render } from 'react-dom';


const ConponentName = (props,context) => {
    return <h1>{ props.text }</h1>
}

let rootEL = document.querySelector('#app');

render(
    <ConponentName text ="hello world"/>,
    rootEL
)
```

优点：stateless component 的创建形式使代码的可读性更好，并且减少了大量冗余的代码，精简至一个render函数，大大的增强了编写组件的便利，并且组件不会被实例化，整体渲染性能得到提升

##  3.写jsx语法,是怎么引入样式名称和style的
> 引入样式，使用className属性；引用style，同样使用style属性，不同的是后面接一个属性对象，属性名称采用驼峰命名法

##  4.react render方法中 return一个组件的时候需要注意什么?
> 仅能有一个顶级标签，返回的html标签应与return同一行，或者html标签用括号包裹

##  5.react 怎么引入一个变量
>  {变量名}


##  6.如何实现组件接口规范约束？
> 使用组件类的`propTypes`属性验证组件实例的属性是否符合要求

##  7.怎么设置组件默认参数
> 使用 ComponentName.defaultProps = {} 设置

##  8.ref是什么?怎么获取ref对应的实例
> 当虚拟DOM插入文档之后，可以使用ref属性来获取真实DOM，获取ref对应实例this.refs[refName]

##  9.react怎么获取DOM节点
> 方法一：通过this.refs.[refName]  获取，ref添加到组件上获取的是组件实例，添加到原生HTML上获取的是DOM；
> 方法二：通过ReactDOM.findDOMNode获取，当参数是DOM，返回值就是该DOM；当参数是Component获取的是该Component render方法中的DOM

##  10.react移除节点的两个方法是哪个?
>

