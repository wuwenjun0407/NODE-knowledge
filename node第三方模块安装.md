# node第三方模块安装
#### 第三方模块：
> 第三方模块网站：https：//www.npmjs.com  node第三方模块的安装统一使用 npm install
```
npm install less 安装在当前目录下（只有当前目录才能使用less模块）
MAC：sudo npm install less

在输入npm init -y

在项目文件中会生成一个package.json的文件，这个文件是当前项目的配置清单
```
>npm install express body-parser 安装body-parser模块方法
>1.以后在安装模块的时候就可以把安装模块的配置信息存储在这个配置文件当中
```
npm install xxx --save-dev(配置的是开发依赖模块)
npm install xxx --save（配置的是生产依赖模块）
```
>2.我们在当前项目中把需要的模块信息都存储在配置信息package.json，到下一个项目的时候，如果下一个项目中需要的依赖模块和这个很相似，你只需要把这个package.json文件复制过去，在下一个项目的命令窗口中执行npm install,就会把之前存储在配置文件中的所有的依赖模块全都下载下来，这就是跑环境。
>
>3.查看当前模块的版本号
```
npm view xxx >xxx.txt
安装指定版本的模块
npm install xxx@2.0.0 --sava-dev
```