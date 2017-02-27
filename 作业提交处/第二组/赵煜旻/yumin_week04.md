## 1.介绍一下React Router
>官方维护的React路由库,通过管理 URL，实现组件的切换和状态的变化。

## 2.使用react router的时候使用那几个属性,这几个属性的是做什么的?
 >Router：一个容器，真正的路由要通过Route组件定义
 >Route： 定义路由，使用`path`定义路径，并用`component 或 components`定义加载的组件

```

 //Router&Route用例1
 <Router>
     <Route path="/" component={IndexContainer} />
     <Route path="/shipTicket/:message" component={ShipTicket} />
 </Router>

//Router&Route用例2 嵌套路由 用户访问/buyRecord 时，会先加载 NavList 组件，然后在它的内部再加载 buyRecord 组件
<Router >
    <Route path="/" componets={NavList} />
        <Route path="/buyRecord" component={BuyRecord} />
        <Route path="/shipTicket/:message" component={ShipTicket} />
    </Route>
</Router>

```

 >IndexRoute：默认情况下加载的子组件

```
 //用户访问根路径时候 默认加载NavList+Home
 <Router>
     <Route path="/" componets={NavList} />
         <IndexRoute component={Home}/>
         <Route path="/buyRecord" components={BuyRecord} />
         <Route path="/shipTicket/:message" components={ShipTicket} />
     </Route>
 </Router>
```

 >Redirect：重定向路由

```
 //用户访问 /shipTicket 时 会默认跳转到 /shipTicket/default
 <Router >
     <Route path="/" componets={NavList} />
         <Route path="/shipTicket/:message" components={ShipTicket} />
         ＜Redirect from="/shipTicket" to="/shipTicket/default" />
     </Route>
 </Router>
```

 >Link:允许用户点击后跳转到另一个路由,类似<a>标签

```
 render(){
     return(
        <ul>
            <li><Link to='/page1'>页面1</Link></li>
            <li><Link to='/page2'>页面2</Link></li>
        </ul>    
     )
 }

```

 >activeStyle/activeClassName：当前匹配路由高亮时的显示效果

```
 render(){
     return(
        <ul>
            <li><Link to='/page1' activeStyle={{color:red}}>页面1</Link></li>
            <li><Link to='/page2' activeClassName="on">页面2</Link></li>
        </ul>    
     )
 }

```


>history属性：用来监听浏览器地址栏的变化，并将URL解析成一个地址对象，供 React Router 匹配

```
//hashHistory:路由将通过URL的hash部分（#）切换，URL的形式类似example.com/#/shipTicket
import { hashHistory } from 'react-router'
<Router history={hashHistory}>
    <Route path="/" component={IndexContainer} />
    <Route path="/shipTicket" component={ShipTicket} />
</Router>

//browserHistory: 浏览器的路由就不再通过Hash完成了，而显示正常的路径example.com/shipTicket
//但需要对服务器改造,否则用户直接向服务器请求某个子路由，会显示网页找不到的404错误。
//如果开发服务器使用的是webpack-dev-server，加上--history-api-fallback参数即可
import { browserHistory } from 'react-router'
<Router history={browserHistory}>
    <Route path="/" component={IndexContainer} />
    <Route path="/shipTicket" component={ShipTicket} />
</Router>

//createMemoryHistory主要用于服务器渲染。它创建一个内存中的history对象，不与浏览器URL互动
const history = createMemoryHistory(location)

```

## 3.使用Link组件的方法,以及它的缺点

>会匹配任何以`/`开始的子路由

```
<Link to="/shipTicket">跳转船票页</Link>
```

## 4.切换路由的几种方式

```
//Link
<Link to="/shipTicket">跳转船票页</Link>

//browserHistory
browserHistory.push(path);

//this.context.router
this.context.router.push(path);
```

## 5.如何手动切换路由,写个例子

```
class IndexContainer extends Component{
    purchase(){
        const path='/shipTicket/es';
        this.context.router.push(path);

    }
    render(){
        return(
            <button onClick={this.purchase.bind(this)}>点我跳转</button>
        )
    }
}
```

## 6.怎么使组件具有context属性

```
class IndexContainer extends Component{
    purchase(){
        const path='/shipTicket/es';
        this.context.router.push(path);

    }
}

IndexContainer.contextTypes={
    router:React.PropTypes.object
}


```

## 7.什么是函数式编程?
>是种编程范式,主要思想是把运算过程尽量写成一系列嵌套的函数调用。特点是函数是第一公民，无副作用，内部不存在状态。

## 8.什么是纯函数?怎么写一个纯函数
>纯函数是这样一种函数，即相同的输入，永远会得到相同的输出，而且没有任何可观察的副作用
```
//以下是不纯的函数，在相同的输入情况下，因为引入了外部变量adultAge，它的最终结果取决于外部变量adultAge
var adultAge=18;

var checkAdult=function(age){
    return age>=adultAge
}

//改造成纯函数
var checkAdult=function(age){
    var adultAge=18;
    return age>=adultAge;
}

```

## 9.什么是函数柯里化?好处是什么
>只传递给函数一部分参数来调用它，让它返回一个函数去处理剩下的参数
>好处:参数复用,延迟执行

```
var add = function(x) {
  return function(y) {
    return x + y;
  };
};

var increment = add(1);
var addTen = add(10);

increment(2);
// 3

addTen(2);
// 12
```

## 10.说一说高阶函数与柯里化函数的区别
高阶函数至少满足下列其一:
-接受一个或多个函数作为输入
-输出一个函数

柯里化函数：将原来接受两个参数的函数变成新的接受一个参数的函数的过程。
