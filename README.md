## 如何将多个js文件合并压缩为一个js文件

#### 为什么要合并、压缩你的JS文件？
在开始之前，先重申一下这个问题。因为经常在帮忙改东西的时候看到HTML页面上引用了N个JS，而通常看到这个就知道这人JS写得有多糟糕了。HTML里穿插一堆JS代码的我就不吐槽了。
加载一个文件消耗的时间可以忽略不计，问题是你显示一个复杂的网页可能会加载N多文件，那我们在我们可以控制的范围内，能少花点时间就少花点呗。用户可是对网页加载的速度很挑剔的！
对JS，一般就会将本地的所有用到的文件合并及压缩。当然，以上对使用requireJS一类的框架加载的除外。

## clean:删除临时文件

uglify:压缩

qunit:测试

concat:合并

任务流程可能是这样的：

task:clean

task:uglify

task:qunit

task:concat

## 安装

前提是你已经安装了nodejs和npm。 你可以在 nodejs.org 下载安装包安装，也可以通过包管理器（比如在 Mac 上用 homebrew，同时推荐在 Mac 上用 homebrew）。

### 安装grunt CLI
` $ npm install -g grunt-cli`

在项目中使用grunt

首先需要往项目里添加两个文件：package.json和Gruntfile.js

package.json:该文件用来为npm存放项目配置的元数据，与grunt关系最大的配置在devDependencies中。

{  
    "name": "cyjs",  
    "version": "0.1.0",  
    "description": "js for k68.org",  
    "homepage": "http://www.k68.org/",  
    "author": "firebaby",  
    "devDependencies": {  
      "grunt": "~0.4.1",  
      "grunt-contrib-jshint": "~0.3.0",  
      "grunt-contrib-concat": "~0.1.1",  
      "grunt-contrib-uglify": "~0.1.2",  
      "grunt-contrib-cssmin": "~0.5.0",  
      "grunt-htmlhint": "~0.9.2"  
    }  
}
Gruntfile.js:注意G的大写，这个文件就是grunt的配置了，其中详细定义了每个任务的细节和执行任务的顺序等。

## 安装grunt

在命令行进入项目所在目录，键入如下命令即可，npm会根据devDependencies中的配置，将需要的grunt及其插件下载到你的项目目录中。

`$ npm install grunt --save-dev`

grunt-contrib-jshint（js语法检查）、grunt-contrib-concat（js合并）、grunt-contrib-uglify（采用UglifyJS压缩js）、grunt-contrib-cssmin（Css压缩合并）、grunt-htmlhint（html语法验查），以上都是常用的插件。

在项目目录下安装插件也可采用如下方式安装：
`$ npm install grunt-contrib-uglify`
`npm install grunt-contrib-cssmin `

##  命令行执行grunt任务   

`$ grunt`

就会按Gruntfile配置的文件进行压缩合并。