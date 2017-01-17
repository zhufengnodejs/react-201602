##1.什么是Git?
>**Git** 是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目

##2.什么是GitHub?
>**GitHub**是一个面向开源及私有软件项目的托管平台，因为只支持Git作为唯一的版本库格式进行托管，故名**GitHub**

##3.git如何从master分支创建develop分支?
-	假设已建立仓库 testGit，默认分支为master
-	创建develop分支` git branch develop` 或 `git checkout -b develop`（创建并切换至develop分支）

##4.git怎么切换分支,切换分支的时候应注意哪些?
> 切换分支命令 `git checkout develop（目标分支名称）`,切换分支之前执行`git status`查看是否有没add和commit的工作，如有则尽可能提交，若不方便则执行`git stash`保留现场然后切换

##5.怎么查看git的状态,结果中的红色表示什么?绿色表示什么?
> 查看git状态命令：` git status` , 结果中红色表示文件仍未提交到缓存区，绿色表示已提交

##6.请描述下如果需要把本地的git仓库以ssh key的方式提交到github的话，需要如何配置？
-	若是以HTTPS方式克隆的仓库，则先执行命令`git remote rm origin`,`git remote add origin git@github.com:xx/xx.git`(use SSH)
-	查看是否已改为SSH方式 `git remote -v`
-	查看本地是否有ssh keys,命令：`cd ~/.ssh/ `,有则进行下一步， 若无则生成，命令：`$ ssh-keygen -t rsa -C "xx@xx.com"`
-	查看当前目录下的文件`ls`，打开公钥`cat id_rsa.pub`,复制文件内容添加至github账户：`settings` → `SSH and GPG keys` →  `New SSH key`
-	提交文件到github，`git add --all` `git commit -m'update'` `git push origin master`

##7.babel-cli这个模块提供了那两个命令?
> babel 和 babel-node

##8.babel是什么?babel能够做什么,能够解析那些语法?
> babel是一个通用的多用途javascript编译器，能够将不同版本的js进行转换，如将es6转换成es5的句法，也可以解析jsx的语法

##9.babel的配置文件是什么? preset 和 plugin 的区别和关联?
> babel配置文件是`.babelrc` ，plugin功能单一，preset是多个plugin的集合

##10.babel 编译单个 文件使用什么命令?
假设原文件为src/index.js，目标文件为dist/index.js
```
babel  src/index.js -o dist/index.js
```
也可以不指定目标路径，直接输出至终端
```
bebel src/index.js
```


##11.babel 编译文件夹 使用什么命令?
假设源文件夹为src，目标文件夹为dist
```
babel src -d dist
```