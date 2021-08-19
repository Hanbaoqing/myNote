# REACT

```react
		React.createElement(arg1,arg2,arg3,...)
   		//arg1: 要创建的元素名（标签）
        //arg2: 该元素的属性
        //arg3及后: 为该元素子节点 若子节点也是元素节点则需要React.createElement
                            
        
         ReactDOM.render(arg1,arg2)
		 //arg1: 要渲染的React元素或组件名（组件标签）
		 //arg2: DOM对象要渲染的位置
```



#### 1.JSX

```jsx
		//{}中可以出现任意JS语法，但是不能出现语句

		//推荐使用（）包裹JSX,避免JSX中自动插入 ;
```



#### 2.组件基础

###### 	state

```javascript
		//state是组件内部私有数据，只能在组建内部使用  通过setState方法修改
```



###### 组件通讯 props

```javascript
		//props用于接收传递给组件的值
		
		//props是一个只读属性
```



###### 三种常见的通讯场景

==父 ==> 子==

```react
		//父组件将需要传递的数据通过 标签属性 的形式直接传给子组件， 子组件通过props接收
		
		Class Prent extend React.Component {
            return <Children name="苏珊" />
        }
```



==子 ==> 父==

```react
		//父组件提供回调函数用于接收数据，传给子组件
		//子组件通过props来调用将需要传递的数据作为参数传入该函数

		Class Prent extend React.Component {
            getData = (data) => {
                console.log(data)
            }
            return <Children getData={this.getData}/>
        }

		Class Clildren extend React.Component {
           state = { age:18 }
            handleClick = () => {
                this.props.getData(this.state.age)
            }
            return <div onClick={this.handleClick}/>
        }
```



==兄弟间==

```react
		//将需要共享的状态和方法提升到最近的父组件中
```





###### Context

```react
		//React.createContext()
		
		// const {Provider,Consumer} = React.createContext()  获取到Provider，Consumer两个组件

		//<Provider value={***} /> 	//包裹组件 value的值为传递的数据

		//<Consumer>{(data) => {}}</Consumer>		//data为value的值
```







#### 组件周期

```react
		//创建时
		constructor	==>	render	==> componentDidMount
		
		constructor: 		创建组件时最先执行			用于初始化state 以及事件处理函数绑定this
        render：			   每次组件渲染时都会触发		  渲染UI
        componentDidMount:组件挂载后（完成渲染后）		  请求 DOM操纵

		
		//更新时
		render	==>	componentDidUpdate
		
		componentDidUpdate:组件更新后
		
        //3种触发render重新渲染的情况
        1.props发生变化时
        2.调用setState时
        3.forceUpdate() 强制更新


		//卸载时
		componentWillUnmount
        组件卸载（从页面消失）		清理工作，比如清除定时器
        
        
```





#### setState

```react
		/setState更新数据是异步的/

		//语法
		1.setState({key:value})

		2.setState( function(state,props){},function(){} )
		参数1函数用于更新state
        
        参数2h
```

