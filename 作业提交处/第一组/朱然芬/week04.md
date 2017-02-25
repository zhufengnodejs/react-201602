## 1.介绍一下React Router
>  `React Router`是完整的React路由解决方案,保持 UI 与URL同步。它拥有简单的API与强大的功能，例如代码延迟加载、动态路由匹配以及帮助建立正确的位置过渡处理

## 2.使用react router的时候使用那几个属性,这几个属性的是做什么的?
> Router，Route，Link，IndexRoute，IndexLink，Redirect，hashHistory，browserHistory，activeStyle/activeClassName
- Router：路由容器
- Route： 定义路由，使用`path`定义路径，并使用`component(s)`指定当前路径匹配时加载的组件
- IndexRoute：默认路由，使用`component(s)`指定加载的组件
- IndexLink： 解决Link会匹配任何以`/`开始的子路由bug
- Redirect：重定向路由
- activeStyle/activeClassName：指定当前路径匹配时高亮显示导航菜单
- hashHistory：history属性，通过哈希值变化来改变路由，不需要配置服务器，不支持服务端渲染，不建议在生产环境使用
- browserHistory：history属性，通过URL变化来改变路由，调用的是浏览器的history，一般用于生产环境

## 3.使用Link组件的方法,以及它的缺点
```
<Link to="/home" activeStyle={{color:'red'}}>Home</Link>
```
缺点：会匹配任何以`/`开始的子路由

## 4.切换路由的几种方式
-	Link
```
 <Link to="/home" activeStyle={{color:'red'}}>Home</Link>
```

-	browserHistory
```
browserHistory.push(path);
```

-	this.context.router
```
this.context.router.push(path);
```

## 5.如何手动切换路由,写个例子
```
import React,{Component,PropTypes} from 'react';
import { browserHistory } from 'react-router';


class Login extends Component {

    constructor(props){
        super(props);
        this.loginFun = this.loginFun.bind(this);
    }
    loginFun(e){
        e.preventDefault();
        const _path = `/user/detail/${this.username.value}`
        // browserHistory.push(_path);
        this.context.router.push(_path);
    }
    render(){
        return (
            <form className="form-horizontal" role="map" onSubmit={ this.loginFun }>
                <div className="form-group">
                    <lable className="col-sm-2 control-label">用户名：</lable>
                    <div className="col-sm-5">
                        <input type="text" className="form-control" ref= { ref => this.username = ref }/>
                    </div>
                </div>
                <div className="form-group">
                    <label className="col-sm-2 control-label">密码：</label>
                    <div className="col-sm-5">
                        <input type="password" className="form-control" ref = { ref => this.password = ref }/>
                    </div>
                </div>
                <div className="form-actions col-sm-offset-3">
                    <button type="submit" className="btn btn-primary">登录</button>
                </div>
            </form>
        )
    }
}

Login.contextTypes = {
    router: PropTypes.object
}

export default Login
```

## 6.怎么使组件具有context属性
```
contextTypes: {
    router: React.PropTypes.object
},

handleFun(event) {
    this.context.router.push(path)
}
```


## 7.什么是函数式编程?
> 不太好解释，跟其他数据类型一样处于平等地位，可以调用赋值传参返回等。

## 8.什么是纯函数?怎么写一个纯函数
> 不依赖于且不改变它作用域之外的变量状态的函数。
```
const add = (x,y) => x+y;
```

## 9.什么是函数柯里化?好处是什么
函数柯里化是指只传递函数的一部分参数来调用它，让它返回一个函数去处理剩下的参数，好处：
- 参数复用：利用柯里化，我们可以固定住其中的部分参数，在调用的时候，这个参数就相当于已经被记住了，不需要再次传递，也就是我们这里输的参数复用。
- 延迟执行：不断的柯里化，累积传入的参数，最后执行

## 10.说一说高阶函数与柯里化函数的区别

 高阶函数是指以一个函数为参数，同时返回一个函数作为函数的返回值，如：
```
const fn = x => x+1;
const highOrderFn = x => y =>  x(y);

console.log(highOrderFn(fn)(1));;//输出：2
```

 而柯里化函数是指传入一部分参数（可能是函数），返回一个函数去处理剩下的参数，返回值可以不是函数，如:
```
const add = x => y => x+y
add(1)(2);//输出：3
```
