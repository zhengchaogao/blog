#CSS模块化


浏览器原生支持css模块化, 但是使用不多：
```css
@import './base.css'
@import './header.css'
@import './content.css'
@import './footer.css'
```
css import语法会有比较严重的性能问题，但不失为一种模块化的利器。  
1. 方便删除、添加模块；  
2. 方便多人协作；  
@import的文件是额外请求的，请求数太多，页面性能不佳，所以，最好的办法就是把模块打包。

###SASS @import语句

SASS预编译会将@import的.scss文件合并打包，有效避免css @import时候的性能问题
```css
@import './base.scss'
@import './header.scss'
@import './content.scss'
@import './footer.scss'
```
当多个模块合并在一起时候，很容易出现选择器命名冲突。如：
```css
//打包后的main.css

//来自./header.scss中定义的logo类
.logo {
	width: 50px;
}
.
.
.
//来自./footer.scss中定义的logo类
.logo {
	width: 100px;
}
```
需要一套命名规范来避免冲突。

###BEM介绍
BEM命名规范约定如下：

**BEM 代表 block、element、modifier。**  
1. block：一个对象（登录表单、导航菜单）；  
2. element：一个块中特定功能的组件（登录按钮、菜单一个栏目）；  
3. modifier：块或元素的不同状态（一个带隐藏的登录表单）； 

**常见的BEM格式像这样:**  
```css
.block {}  
.block__element {}  
.block--modifier {}  
.block_element--modifier {}
```
**SASS写BEM的原始写法：**
```css
.person {

	&__hand {
	}

	&--female {
 	}

 	&--female__hand{
 	}
}
```

```css
//编译为css
.person {
}
.person__hand {
}
.person--female {
}
.person--female__hand {
}
```
**postcss 中 postcss-bem 插件：**
postcss-bem 中设置 bem({style: 'bem'})。语法：  
1. 生成block @component；  
2. 生成element @descendent；  
3. 生成modifier @modifier；  

**BEM中的问题和误区**  

id、后代选择器   
1. id选择器原则上留给js；  
2. 后代选择器在写block时候是不用的，在block嵌套时候，会用后代选择器；   
  
误区    
1. 一个Block下的所有Element无论相互层级如何,都要摊开扁平的属于Block；  
2. BEM 最多只有 B+E+M 三级,不可能出现 B+E+E+..+E+M 超长class名,也要求E不能同名；  

###PostCSS
TODO
###react中的css module
TODO