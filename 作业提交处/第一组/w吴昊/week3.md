##  1.state和props的用法和区别?

props：数据通过 props 从拥有者流向归属者一般用于父组件向子组件通信，在组件之间通信使用。
state： 一般用于组件内部的状态维护，更新组建内部的数据，状态，更新子组件的props等。

##  2.stateless component的定义和有点是什么？

##  3.写jsx语法,是怎么引入样式名称和style的
样式名称用className
style={驼峰}
##  4.react render方法中 return一个组件的时候需要注意什么?

##  5.react 怎么引入一个变量

##  6.如何实现组件接口规范约束？

##  7.怎么设置组件默认参数

##  8.ref是什么?怎么获取ref对应的实例

##  9.react怎么获取DOM节点
this.refs.[refName]
ReactDOM.findDOMNode

##  10.react移除节点的两个方法是哪个?
在render内return null
ReactDOM.unmountComponentAtNode(dom)
