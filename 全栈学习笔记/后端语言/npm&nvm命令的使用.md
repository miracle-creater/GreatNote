## NPM命令的使用

### NPM下载

> LTS:  Long Term Support
>
> [官方网址](https://nodejs.org)  https://nodejs.org
>
> [安装npm组件](https://www.npmjs.com/)  https://www.npmjs.com

NPM是随同NodeJS一起安装的包管理工具，以便解决NodeJS代码部署上的很多问题

- 允许用户从NPM服务器下载别人编写的**第三方包**到本地使用。
- 允许用户从NPM服务器下载并安装别人编写的**命令行程序**到本地使用。
- 允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用。

### 配置环境变量

**意义** ：在于在任何场景都可以使用该命令

1. 用来检测安装版本，是否安装成功

    ```
    npm -v
    ```

2. 安装或者更新

> 从官网进行安装
> npm install npm -g
>
> 安装淘宝镜像
> npm install -g cnpm --registry=https://registry.npm.taobao.org
>
> 之后就可以通过cnpm代替npm进行安装
>
> > 注：安装时默认会把文件安装到当前文件夹内，建议更改当前路径后安装到项目目录

3. 其它功能

> npm list -g  查看全局安装的模块
>
> npm uninstall express  卸载nodejs模块
>
> npm search express 搜索模块
>
> npm publish 发布模块
>
> npm init  创建JSON文件，初始化开发环境
>
> npm list  列出已经安装模块
>
> npm update 升级当前目录下的项目的所有模块

```
npm install gulp@3.9.1 --save-dev
npm安装gulp  
--save：在当前文件夹下
-dev    将安装的信息保存在package.json中
gulp@3.9.1下载3.9.1版本
简写:
npm i gulp@3.9.1 -D
```



### 其它相关组件的安装

#### PostCSS

```
npm install postcss-cli -g
```

> PostCSS 可以理解为一个运行环境，用于使用JavaScript改变CSS
>
> 官方解释：A tool for transforming CSS with JavaScript

#### Animate.css

```
npm install animate.css --save
```

> animate.css 是一些CSS动画的集成

#### postcss-sprites

```cnpm i stylelintcnpm i stylelint
cnpm i postcss-sprites
```

> 将图片自动合成为一张图片

```js
const sprites = require('postcss-sprites');
module.exports = {
	plugins :[
		cssnext,
		stylelint({
            "rules" : {
            "color-no-invalid-hex" true;
            }
		}),
		sprites({
		spritePath : './dist'
		})
	]
}
```

#### stylelint

> - cnpm i stylelint
>
> - 进行css纠错

```js
const cssnext = require('postcss-cssnext');
module.exports = {
	plugins :[
		cssnext,
		stylelint({
            "rules" : {
            "color-no-invalid-hex" true;
            }
		})
	]
}
```

#### postcss-cssnext

```
cnpm i postcss-cssnext
```

对css进行降级，从而支持更多浏览器

```js
const cssnext = require('postcss-cssnext');
module.exports = {
	plugins :[
		cssnext
	]
}
```

#### autoprefixer

命令行安装

```
cnpm i autoprefixer
```

自动添加浏览器前缀，进行浏览器兼容

```javascript
//再配置文件中引入
const autoprefixer = require('autoprefixer');
module.exports = {
	plugins :[
		autoprefixer({
			browsers : ['> 0%']//对所有浏览器兼容
		})
	]
}
```

#### postcss-import

命令行安装

```
cnpm i postcss-import
```

对于多个css文件进行合并

```
const postcss = require('postcss-import');
module.exports = {
	plugins :[
		postcss
	]
}
```

#### cssnano

命令行安装

```
cnpm i cssnano
```

对于css进行压缩

```
const postcss = require('postcss-import');
module.exports = {
	plugins :[
		cssnano
	]
}
```

## nvm命令的使用

> nvm是用来对node进行版本控制的工具
>
> windows上的nvm和linux&MacOS上的nvm工具不是一个项目，不是一队人马

#### nvm(Linux、Unix、OS  X)的安装

安装教程网址：https://github.com/creationix/nvm

#### nvm(Windows)

安装教程网址：https://github.com/coreybutler/nvm-windows

### 命令行工具

> nvm install node & nvm install latest (安装最新版本的node)
>
> nvm list  &   nvm ls 当前所拥有的npm版本
>
> nvm use taobao 切换到淘宝镜像
>
> cnpm install -g nvm  全局安装nvm命令
>
> nvm -v 当前nvm工具的版本
>
> nvm use 8.4.0 使用8.4.0版本的node
>
> nvm uninstall 版本号 卸载该版本的node.js


