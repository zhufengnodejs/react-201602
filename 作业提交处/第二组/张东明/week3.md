##  1.state和props的用法和区别?
state是用来管理组建状态的，用setState来设置，this.state来调用。props则是用来保存从上一级组件传来的属性的，一般认为是只读的，用this.props来调用。

##  2.stateless component的定义和优点是什么？
无状态组件只实现render而不实现生命周期其他方法。优点是简单可复用。

##  3.写jsx语法,是怎么引入样式名称和style的
使用css in Js。
```javascript
const styles={"width":"100px"}
<div style=styles>
</div>
```
##  4.react render方法中 return一个组件的时候需要注意什么?
return组件只能有一个根元素
如果dom结构比较复杂，最好把标签用()包起来。

##  5.react 怎么引入一个变量
用setState保存为state的一个属性

##  6.如何实现组件接口规范约束？
对于组件Profile
Profile.propTypes={
url:PropTypes.string //指定该接口为string类型
}

##  7.怎么设置组件默认参数
Profile.defaultProps={
url:"http://www.zhufeng.com"
}

##  8.ref是什么?怎么获取ref对应的实例
比如组件<range ref="rangeOne" />可以在其夫组件中通过this.refs.rangeOne的方式获取到

##  9.react怎么获取DOM节点
使用8中所提到的方式之后，调用组件上的getDOMNode()可以获取DOM节点

##  10.react移除节点的两个方法是哪个?
1.render方法中return null;
2.ReactDOM.unmountComponentAtNode(container)
