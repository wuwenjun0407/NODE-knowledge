# node 模块 npm安装

@(NODE)


### h5中js多线程？
#### 怎么解决node的异步问题
>callback


##### node 不具有兼容的问题

##### 在node中能用异步，绝不用同步，解决异步的方法就是回调函数。

##### 异步永远在同步之后执行，如果同步代码执行不能完成，异步永远不能执行

>非阻塞是异步的前置条件

##### node是单线程--->node是基于js的 异步

>多线程（感觉像是同一时间干很多事情，快速切换上下文）
>只要在文件中，可以不用声明直接使用的，都叫全局对象
>服务端没有window，点击事件，ajax
>服务端有global，
>process 进程
>buffer 缓存区（表示内存）


### 模块化

>js中实现模块化，单例，闭包
>单例：缺点：不能保证一定不冲突，会导致调用过长，require（AMD），seajs(CMD)，import,export，不兼容
>没有块级作用域

### node 自带模块化 commonjs规范

- 怎么定义一个模块（每个js都是一个模块，在每个文件 外面增加一个闭包）
- 如何导出一个模块（module . exports/exports）
- 如何引用一个模块 require（）
>exports,module,require,__dirname,__filename 这五个也是全局对象。通过闭包传进来的形参
```
(function(){

})(exports,require,module,__dirname,__filename)

```

### 模块分类
- 文件模块（我们自己写的模块）引用方法：require（“./文件”）
- 第三方模块（别人写的，需要下载npm下载块）引用方法：直接引用
 -  全局安装（只能在命令行下使用，会提供给你一个全局命令）node切换源的工具
      ```
      npm install xxx -g
      nrm test
      nrm use cnpm
      ```
  -   本地安装（在当前项目下使用）
	     -  npm init 记录所有依赖的 生成package.json,可能会导致安装到上级目录，名字不能有中文，大写，特殊字符
       -    开发依赖 只在开发时应用 --save-dev 简写（-D）
       -    项目依赖 --save 简写（-S）
       -  卸载 npm uninstall 模块名字  类型（--save-dev/--save）
       -  查看模块版本 npm info vue
       -  指定版本安装 npm install vue@1.0.0 --save
- 内置模块，核心模块，node自带的

>npm node package manager 管理node的包（很多js文件）的，安装node自带npm

### yarn 需要npm来下载（主流）
>安装一次即可
```
npm install yarn -g
```
>初始化 package.json
```
yarn init -y
```
>本地安装
-   开发依赖 yarn add less --dev
-  项目依赖  yarn add jquery
>删除
-  yarn remove less --dev
-  yarn remove jquery
>全部安装
```
yarn install
```

### 发布包(必须要是别人没有发布过的，包里需要有一个package.json)

>需要登录到官方npm上
```
nrm use npm
```
>注册账号
```
npm addUser
```
