#BEM介绍

**BEM 代表 block、element、modifier。**  
1. block：一个对象（登录表单、导航菜单）；  
2. element：一个块中特定功能的组件（登录按钮、菜单一个栏目）；  
3. modifier：块或元素的不同变化（一个带隐藏的登录表单）； 

**常见的BEM格式像这样:**  
```css
.block {}  
.block__element {}  
.block--modifier {}  
.block_element--modifier {}
```
**SASS写BEM的原始写法：**
```css
//correspondence 下有list、preview组件，以及full-size变种。

.correspondence {

	&__list {
	}

	&__preview {
 	}

 	&--full-size{
 	}
}
```