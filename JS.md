# JS

#### 	1.隐式转换

代表空或否定的值会被转化成false，其余为true

```javascript
			"" , NaN , 0 , undefined , null
```



###### 		对象与布尔值比较：

​		比较时，对象会先转化为字符串，然后再转化为数字

```javascript
		[] == true // false    []转化为'',然后转化为数字0, true转化为数字1
```



###### 对象与字符串比较：

​		比较时，对象会先转化为字符串，然后进行比较

```javascript
		[1,2,3] == "1,2,3"	//true 
```



###### 对象和数字比较：

​		比较时，对象会先转化为字符串，然后再转化为数字

```javascript
		[1] == 1 // true    []转化为'1',然后转化为数字1
```

==注意==

```javascript
		[] == false		// [] 先转话为 "" 
		![] == false	// 因为多了 ！, 所以 []直接转换为布尔值 true
```



#### 2.函数

###### 	创建方式：

```javascript
		1. function 函数名() {} 			//命名函数
		2. const 变量名 = function() {}	//匿名函数
        3. const 变量名 = new Function()
        4. const 变量名 = () => {}			//箭头函数
```

函数需要返回值，否则函数结果为undefined



###### 高阶函数：

将函数作为参数或返回值（常见的应用场景——==回调函数==）



###### 闭包：

当一个作用域访问了另外一个作用域中的变量时，就会有闭包的产生，变量所在的函数称为闭包函数。

本质：产生的原因就是函数的嵌套。

```javascript
		function fn() {
            var num = 10;
            function fun() {
                console.log(num)
            }
            fun()
        };

		fn()
```

立即执行函数就是闭包的一种典型应用



###### arguments

JS中当前函数的一个内置对象，存放了所有传递的过来的实参





#### 3.对象

###### 	创建方式：

```javascript
		1. var obj = {}				//字面量
        2. var obj = new Object()	// new
        3. var 变量名 = new 构造函数	//构造函数
        
        function 构造函数() {
            this.属性名 = 值,
            this.方法名 = function() {}
        }
```



###### 	属性和方法：

调用属性和方法：obj.属性名（obj['属性名']）  /  obj.方法名

追加属性和方法：obj.属性名/方法名 = 值

遍历对象：for	in 循环





#### 4.ES6中类与对象

###### 	定义：

```javascript
		class 类名 {};			const *** = new 类名（）

		class Car {
            constructor(){
                this.price = 100
            }
            run(){
                return "******"
            }
        }

		//其中constructor 是类的构造函数，用于传递参数，生成实例对象，在通过 new 生成实例时自动执行
		//类的其他方法不需要写在 contructor 中
		//constructor中 this 指向实例对象
```



###### 	继承（extends）：

```javascript
		class Father {
            constructor(x,y){
                this.x = x;
                this.y = y
            }
            sum() {
                return this.x + this.y
            }
        }

		class Son extends Father {
            constructor(a,b){
                super(a,b)
                this.a = a;
                this.b = b
            }
        }

		const son = new Son(1,2)	// {x:1,y:2,a:1,b:2}
        
        //super() 用于访问父类上的函数
        
        //若super中无参数，则x,y为undefined
        //若子类中无独有的属性 constructor方法可以不写 此时不需要 super
```



子类会继承父类上的属性和方法，子类在调用方法时，会先查看自身是否拥有该方法，若没有则在父类上找；若子类拥有独有的属性，则需要写constructor，此时必须先使用super方法
