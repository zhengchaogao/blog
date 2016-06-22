#React入门


###ReactDOM.render()方法
将模版转化为html
```javascript
ReactDOM.render(
	<h1>lalala11111</h1>,
	document.getElementById('example')
);
```
####jsx语法
遇到html的<>标签就是html语法，遇到代码块{}就是javascript语法；

###react的组件
react组件可像html标签一样，在网页中插入组件。
```javascript  
//创建HelloMessage组件 
var HelloMessage = React.createClass({
	render: function () {
		return (
			<h1>hello {this.props.name}</h1>
		)
	}
});

//插入一个HelloMessage组件实例
ReactDOM.render(
	<HelloMessage name="gaozhengchao" />,
	document.getElementById('example')
);
```
其中this.props用来获取属性。当属性为class和for时候，要改成className和htmlFor。    
并且每个组件只能有一个顶层标签，作为组件树的root。
###组件属性this.props
1. this.props包含组件中的所有属性。   
2. this.props.children可以获取组件下的子节点。值为undefined、object、array。  

###组件属性验证propTypes、getDefaultProps
组件属性可以是字符串、数字、对象、函数等等。  
####propTypes用来验证组件属性。
```javascript  
//创建HelloMessage组件 
var HelloMessage = React.createClass({
	// 验证属性
	propTypes: {
		name: React.PropTypes.string.isRequired
	},
	render: function () {
		return (
			<h1>hello {this.props.name}</h1>
		)
	}
});

//插入一个HelloMessage组件实例
ReactDOM.render(
	<HelloMessage name="gaozhengchao" />,
	document.getElementById('example')
);
```
React.PropTypes.string.isRequired规定了name属性必须为string类型且不可少。
####getDefaultProps用来设置属性的默认值
```javascript  
//创建HelloMessage组件 
var HelloMessage = React.createClass({
	// 设置默认值
	getDefaultProps: function() {
		return {
			name: 'world!'
		};
	},
	render: function () {
		return (
			<h1>hello {this.props.name}</h1>
		)
	}
});

//插入一个HelloMessage组件实例
ReactDOM.render(
	<HelloMessage />,
	document.getElementById('example')
);
```