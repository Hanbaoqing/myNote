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

		//<Consumer>{(data) => {}}</Consumer>		//data为value的
```

