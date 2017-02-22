##  1.state和props的用法和区别?
>state 是组件内部用来做状态维护,一旦这里的值发生了变动，会自动触发组件的render方法

>props 主要用来描述组件的特性,一旦定义不随用户的互动而改变的值，跟在this.props 后面命名，通常是一一对应的，但this.props.children例外，它表示组件所有的子节点。

```

class Counter extends Component{
  constructor(){
    super();
    this.state={
      num:0//用作状态维护，用户点击按钮就会更新这个值
    }
  }
  update(){
    this.setState({
      num:this.state.num+1
    })
  }
  render(){
    return(
    <div>
      <p>已被点击:<span></span>次</p>
      //this.props.txt 接受传值，并不再改变
      <button onClick={this.update.bind(this)}>{this.props.txt}</button>
    </div>

    )
  }
}

render(<Counter txt="点我"/>,document.getElementById('container'))

```

##  2.stateless component的定义和有点是什么？
指的是无状态组件，增强组件的方便性，也提升了整体的渲染性能。
```

const Profile = ({name,age}) => (
  <div >{name},{age}</div>
);

ReactDOM.render(
  <Profile name='alex',age='13' />,
  document.getElementById('container')
);

```

##  3.写jsx语法,是怎么引入样式名称和style的

```

第一种style属性直接写在组件内

class Profile extends Component{
  render(){
    const nameStyle={
      color:"red",
      fontSize:"20px"
    }
    return (
      <div style={nameStyle}>{this.props.name}</div>
    )
  }
}

render(<Profile name="alex"/>,document.getElementById('container'));

```

```

第二种className+引用css文件形式

class Profile extends Component{
  render(){
    return (
      <div className="cssName">{this.props.name}</div>
    )
  }
}
render(<Profile name="alex"/>,document.getElementById('container'));

```

##  4.react render方法中 return一个组件的时候需要注意什么?
>有多个子元素时，必须由一个顶级标签包裹起来

##  5.react 怎么引入一个变量
>通过this.props 来传递变量,Profile例子中已有演示 this.props.name

##  6.如何实现组件接口规范约束？

```

class Profile extends Component{
  render(){
    return (
      <div className="cssName">{this.props.name},{this.props.id}</div>
    )
  }
}
render(<Profile name="alex" id="2"/>,document.getElementById('container'));

//接口限制 不符合会报错
Profile.propTypes={
  name:React.PropTypes.string,
  id:React.PropTypes.number.isRequired//isRequired强制要求必须传值
}

```

##  7.怎么设置组件默认参数

```

class Profile extends Component{
  render(){
    return (
      <div className="cssName">{this.props.name},{this.props.id}</div>
    )
  }
}
render(<Profile name="alex" id="2"/>,document.getElementById('container'));

//默认值 没有传值时会用这里的
Profile.defaultProps={
  name:"default",
  id:"0"
}

```

##  8.ref是什么?怎么获取ref对应的实例

```

class Profile extends Component{
  showcName(){
    //获取对应的实例
    console.log(this.refs.myProfile)
  }
  render(){
    return (
      <div>
        <div className="cssName" ref="myProfile">{this.props.name}</div>
        <button onClick={this.showName.bind(this)}>click</button>
      </div>

    )
  }
}

```

##  9.react怎么获取DOM节点

>第一种：this.refs.[refName]
>第二种：ReactDOM.findDOMNode(this.refs.myProfile);

##  10.react移除节点的两个方法是哪个?

```

第一种通过state控制状态，返回render()渲染时返回null
render(){
  if(this.state.destroyed){
    return null
  }
}

第二种
remove(){
  ReactDOM.unmountComponentAtNode(document.getElementById('container'))
}

```
