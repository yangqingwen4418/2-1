# 简答题

**1、谈谈你对工程化的初步认识，结合你之前遇到过的问题说出三个以上工程化能够解决问题或者带来的价值。**

答：

认识：一切以提高效率、降低成本、保证质量为目的的手段都属于工程化。工程化不等于某个工具。工程化解决的问题：能够兼容使用ES6+新特性；能够使运行环境直接友好支持Less/Sass/PostCSS等，增强编程友好性；能使运行环境直接支持使用模块化的方式提高项目的可维护性；部署上线前不需要手动压缩代码及资源文件；多人协作开发，可以统一大家的代码风格且保证从仓库中pull回来的代码质量；部分功能开发时不再需要等待后端服务接口提前完成；

价值：减少了不必要的重复工作，极大的提高了效率，降低了成本，保证了质量。

**2、你认为脚手架除了为我们创建项目结构，还有什么更深的意义？**

答：

脚手架是前端工程化的发起者。除了创建项目基础结构外，还提供项目规范和约定，是项目具有相同的组织结构、相同的开发范式、相同的模块依赖、相同的工具配置、相同的基础代码、



# 编程题

1、概述脚手架实现的过程，并使用 NodeJS 完成一个自定义的小型脚手架工具

答：

用yeoman实现脚手架过程：

​	1、全局安装：npm install yo --global 或 yarn global add yo

​	2、安装对应generator：npm install generator-node --global 或 yarn global add generator-node

​	3、通过yo运行generator cd到相应目录， mkdir创建项目目录，然后执行yo node命令

​	4、完成各种输入后自动安装。

​	5、然后安装sub-generator：

​			首先安装：命令行输入：yo node:cli命令，后选择yes,重写package.json

​			然后执行yarn link连接到全局

​			然后执行yarn安装依赖

​			然后执行模块名（或称文件夹名）--help验证是否成功，如果报错，再重复执行上一步

​			登陆官方文档http://github.com/yeoman/generator-node查看该generator下有无一个子集的					生成器即可。

​	6、然后创建generator模块：

​			目录结构：generators/app/index.js(默认生成器会实现),如果还有子生成器，创建				g

​						enerators/app/component/子生成器目录名/index.js

​			名称格式：generator-<name>

​			创建目录：mkdir generator-<name>，然后cd到该目录

​			执行yarn init命令

​			执行yarn add yeoman-generator命令

​			命令行执行code . 命令用vscode打开该目录，创建文件：generators/app/index.js

​			回退到generator-<name>目录命令行输入yarn link连接到全局

​			返回上级目录，在与generator-<name>目录的同级目录创建新文件夹mkdir 项目名，并cd到该					项目目录。

​			执行yo <name>(生成器名字)后回车创建了相应的文件

​			根据模板创建文件的方法：

​					现在generators/app目录下创建template/xxx.txt模板文件（所有模板放入template目								录，然后根据txt文件中的EJS语法动态输出数据）

​					更改app/index.js文件的方法：this.fs.copyTpl(tmpl,output,context)

​					最后在项目目录下执行 yo <name>

​			

2、尝试使用 Gulp 完成项目的自动化构建

首先，用npm init初始化项目目录，生成package.json文件。

其次，在项目根目录创建gulpfile.js文件。

然后，再安装以下插件：

​			gulp: npm i gulp --save-dev

​			browser-sync: npm i browser-sync --save-dev

​			gulp-rename: npm i gulp-rename --save-dev

​			gulp-swig: npm i gulp-swig --save-dev

​			gulp-sass: npm i gulp-sass --save-dev

​			gulp-babel: npm i gulp-babel --save-dev	和		

​								npm i --save-dev gulp-babel @babel/core @babel/preset-env

​			gulp-imagemin: npm i gulp-imagemin --save-dev

​			del：npm install del --save-dev

​			gulp-loade-plugins : npm i glup-loader-plugins --save-dev

​			gulp-useref: npm igulp-useref --save-dev

​			gulp-htmlmin、gulp-uglify、gulp-clean-css: npm igulp-htmlmin/gulp-uglify/gulp-clean-css 					--save-dev

然后，在gulpfile.js目录自定义函数来完成相应HTML、css、less、sass、js、图片等格式任务的转换			或复制、压缩。

最后，把执行命令定义在package.json中的scripts位置，执行该命令即可。执行结果如下：

![image-20200824123407034](C:\Users\qinhe\AppData\Roaming\Typora\typora-user-images\image-20200824123407034.png)			

