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
react组件可像html标签一样，在网页中插入组件。组件其实并非真正的dom，而是虚拟dom。每次dom的变动都
是先发生在虚拟dom上，然后在将实际变动的部分，反映到真实的DOM里（dom diff算法）。
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
2. this.props.children可以获取组件下的子节点。值类型为undefined、object、array。  

###组件属性propTypes、getDefaultProps
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
设置name属性的默认值为world！
###组件获取真实的DOM
组件是虚拟DOM，当需要获取真实的DOM节点时候，用ref属性：
```javascript  
var HelloMessage = React.createClass({
	// 事件回调
	handleClick: function() {
		var value = this.refs.username.value;
		console.log(value);
	},
	render: function () {
		return (
			<div>
				<input type="text" ref="username" />
				<input type="button" onClick={this.handleClick} />
			</div>
		)
	}
});

//插入一个HelloMessage组件实例
ReactDOM.render(
	<HelloMessage />,
	document.getElementById('example')
);
```
上例中button绑定handleClick事件，打印出username的值。this.refs.username取得真实input DOM的引用。

###React状态机
React将组件看成一个状态机，每当state改变的时候，触发重新渲染ReactDOM.render()。   
关于状态机API
1. this.state读取状态。   
2. getInitialState() 定义初始状态。   
3. this.setState()修改状态。   
```javascript  
var HelloMessage = React.createClass({
	// 初始状态
	getInitialState: function() {
		return {
			liked: true
		};
	},
	handleClick: function(e) {
		// 修改状态
		this.setState({
			liked: e.target.value
		})
	},
	render: function () {
		return (
			<div>
				<input type="text" value={this.state.liked} onChange={this.handleClick} />
			</div>
		)
	}
});
//插入一个HelloMessage组件实例
ReactDOM.render(
	<HelloMessage />,
	document.getElementById('example')
);
```
###React组件的生命周期

组件生命周期分三个状态
1. mounting：已插入真实DOM;  
2. updating：正在被重新渲染;   
3. unmounting: 已被移除真实DOM;   

每种状态都提供了两种处理函数 will 和 did，will函数在进入状态前、did函数在进入状态后。   
1. componentWillMount()     
2. componentDidMount()     
3. componentWillUpdate(object nextProps, object nextState)   
4. componentDidUpdate(object prevProps, object prevState)     
5. componentWillUnmount()     

此外还有两种特殊的状态处理函数   
1. componentWillReceiveProps(object nextProps): 已加载组件收到新属性参数时调用     
2. shouldComponentUpdate(object nextProps, object nextState): 判断组件是否重新渲染时调用    

