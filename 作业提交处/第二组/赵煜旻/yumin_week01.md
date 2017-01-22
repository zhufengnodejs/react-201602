##1.什么是Git?
> 一款免费，开源的分布式版本控制系统。

##2.什么是GitHub?
> Github是用Git做版本控制的代码托管平台

##3.git如何从master分支创建develop分支?
```
git branch develop
```

##4.git怎么切换分支,切换分支的时候应注意哪些?
```
切换分支：git checkout branch_name
```
> 用`git status`查看当前分支状态，确保分支是nothing to commit状态

##5.怎么查看git的状态,结果中的红色表示什么?绿色表示什么?
```
git status
```
> 红色代表没有add（添加到暂存区），绿色代表没有commit（提交到版本库中）

##6.请描述下如果需要把本地的git仓库以ssh key的方式提交到github的话，需要如何配置？
- 第一步：生成一个ssh（`ssh-keygen -t rsa` ）
- 第二步：复制公钥到github SSH and GPG keys中
- 第三步：`git add`
- 第四步：`git commit -m`
- 第五步：`git push origin master`

##7.babel-cli这个模块提供了那两个命令?
> bable,babel-node

##8.babel是什么?babel能够做什么,能够解析那些语法?
> Babel是一个广泛使用的Javascript转码器，可以将ES6代码转为ES5代码，从而在现有环境执行。

##9.babel的配置文件是什么? preset 和 plugin 的区别和关联?
> .babelrc,plugin是插件，preset是plugin的集合。

##10.babel 编译单个 文件使用什么命令?
```
babel 输入文件名 --out-file 输出文件名
```
> 例: `babel input.js --out-file output.js`
> 就会把当前目录中的input.js文件 编译到当前目录下的output.js中

##11.babel 编译文件夹 使用什么命令?
```
babel 输入文件夹 --out-dir 输出文件夹
```
>例：babel src --out-dir dist

> 会把子目录src的内容 编译到 dist目录中，
> 如果在dist 后面加-w参数 
```
babel src --out-dir dist -w 
```
>只要src目录中的文件发生改变 系统就会 自动编译到dist目录中