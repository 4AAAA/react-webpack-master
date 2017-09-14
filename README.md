# react-webpack-master
React+Webpack+ES6从环境搭建到HelloWorld
React是一个Facebook和Instagram用来创建用户界面的JavaScript库,是现在最热门的前端框架。Webpack 是当下最热门的前端资源模块化管理和打包工具。它可以将许多松散的模块按照依赖和规则打包成符合生产环境部署的前端资源。还可以将按需加载的模块进行代码分隔，等到实际需要的时候再异步加载。通过 loader 的转换，任何形式的资源都可以视作模块，比如 CommonJs 模块、 AMD 模块、 ES6 模块、CSS、图片、 JSON、Coffeescript、 LESS 等。ECMAScript 6（以下简称ES6）是JavaScript语言的下一代标准。因为当前版本的ES6是在2015年发布的，所以又称ECMAScript 2015。

webpack的模块化，react的组件化，以及es2015的各种新特性都很吸引人，网上也有很多入门的资料,但是很多都是偏概念的,本文将结合实际开发来搭建整个环境。下面我们进入正题:
环境搭建:

1.从官网下载最新版本的node.js安装
官网下载地址:

http://nodejs.org/en/

官网需要翻墙,如果没有翻墙的同学可以到nodejs中文网下载,下载地址:

http://nodejs.cn

如果你需要使用Homebrew安装nodejs,请参考我的另一篇博客:

http://blog.csdn.net/pcaxb/article/details/52046438

安装完Node之后，为了保证速度，需要使用淘宝镜像，命令如下:

（1）npm config set registry "http://registry.npm.taobao.org"  
（2）npm config list  可以查看配置  
2.安装完nodejs之后,打开终端,执行命令:
  npm install webpack -g  
  
  -g的意思是安装全局的webpack,但是我们实际的开发中还需要针对单个的项目进行webpack安装,执行命令:
  npm install webpack --save-dev  
  
  创建项目:
  1.创建一个根目录，目录名为react-webpack-master,执行命令:
  mkdir react-webpack-master创建目录  
  cd react-webpack-master/ 切换到该目录下  
  
  2.使用 npm init 初始化，生成 package.json 文件：执行命令:
  npm init 自定义创建package.json  
  npm init -yes 可以创建默认的package.json  
  
  3.现在我们的项目已经创建好了,接下来我们来添加依赖包及插件
    (1)局部安装Webpack,执行命令：
       npm install webpack --save-dev 
    (2)安装React,--save 命令用于将包添加至 package.json 文件,执行命令:
       npm install react react-dom --save-dev     
    (3)安装babel插件,babel插件是webpack需要的加载器,如果没有这几个加载器我们的jsx语法，和es2015语法就会报错。
       npm install babel-loader babel-preset-es2015 babel-preset-react --save-dev  
       
webpack.config.js配置:

entry: 指定打包的入口文件 main.js。
output：配置打包结果，path定义了输出的文件夹，filename则定义了打包结果文件的名称。
devServer：设置服务器端口号为 8181，端口后你可以自己设定 。
module：定义了对模块的处理逻辑，这里可以用loaders定义了一系列的加载器，以及一些正则。当需要加载的文件匹配test的正则时，就会调用后面的loader对文件进行处理，这正是webpack强大的原因。

webpack-dev-server允许我们可以把本地项目跑在像nginx那样的web服务器上，更重要的是我们可以在package.json文件内定义scripts，同时修改webpack的配置文件来达到自动刷新的效果。
安装webpack-dev-server执行命令:

npm install webpack-dev-server --save-dev  

在package.json文件中为scripts添加,方便使用命令:
"scripts": {  
  "build": "webpack",  
  "dev": "webpack-dev-server --devtool eval --progress --colors --content-base build"  
}  

这里的命令是webpack,如果需要压缩编译的话,将webpack改成webpack -p

最终package.json文件如下

这里有一点提醒大家，package.json中name不能跟我们的模块和项目文件目录同名

项目代码编写：

1.index.html代码

2.main.js代码

3.Tab1.js代码

代码编译结束:

1.根目录下执行命令
npm run dev  

2.浏览器直接访问:

http://localhost:8181/index.html


