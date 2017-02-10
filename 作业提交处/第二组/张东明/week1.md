## 1.什么是Git?    
git 是一个版本管理器，方便管理系统
## 2.什么是GitHub?
github是使用git作版本控制的远程仓库
## 3.git如何从master分支创建develop分支?
```
git branch develop
```
## 4.git怎么切换分支,切换分支的时候应注意哪些?
想切换到develop分支
```
git checkout develop
```
## 5.怎么查看git的状态,结果中的红色表示什么?绿色表示什么?
看状态
```
git status
```
其中红色是没有提交到暂存区的，绿色是提交过的。
## 6.请描述下如果需要把本地的git仓库以ssh key的方式提交到github的话，需要如何配置？
1.查看remote  
2.删除https的remote    
3.添加ssh的remote  
4.用cd ~/.ssh =>ls命令查看是否生成过密钥    
5.如果没有的话用ssh-keygen -t rsa -C ”{邮箱}“的方式生成一个     
6.将公钥添加到github的账户上
## 7.babel-cli这个模块提供了那两个命令?
 * babel:使用babel编译文件
 * babel-node:编译并用node运行文件  
## 8.babel是什么?babel能够做什么,能够解析那些语法?
是一个js编译器，可以配合它的presets和plugins来把react,es6等语法的js代码
编译成可供当前浏览器运行的代码。
## 9.babel的配置文件是什么? preset 和 plugin 的区别和关联?
配置文件.babelrc用来配置babel如何编译文件，里面可以写preset,plugin等来告诉babel如何编译文件
plugin功能单一，preset集成多个plugin完成某项任务。
比如babel-preset-es2015就是由解析各个es2015语法的plugin组成
## 10.babel 编译单个 文件使用什么命令?
babel {源文件} --out-file {目标文件}
## 11.babel 编译文件夹 使用什么命令?
babel {源路径} --out-dir {目标路径}