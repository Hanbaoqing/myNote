# 	JS

#### 	1.隐式转换

代表空或否定的值会被转化成false，其余为true

```javascript
			"" , NaN , 0 , undefined , null
```



###### 		对象与布尔值比较

​		比较时，对象会先转化为字符串，然后再转化为数字

```javascript
		[] == true // false    []转化为'',然后转化为数字0, true转化为数字1
```



###### 对象与字符串比较

​		比较时，对象会先转化为字符串，然后进行比较

```javascript
		[1,2,3] == "1,2,3"	//true 
```



###### 对象和数字比较

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

###### 	创建方式

```javascript
		1. function 函数名() {} 			//命名函数
		2. const 变量名 = function() {}	//匿名函数
        3. const 变量名 = new Function()
        4. const 变量名 = () => {}			//箭头函数
```

函数需要返回值，否则函数结果为undefined



###### 高阶函数

将函数作为参数或返回值（常见的应用场景——==回调函数==）



###### 闭包

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

###### 	创建方式

```javascript
		1. var obj = {}				//字面量
        2. var obj = new Object()	// new
        3. var 变量名 = new 构造函数	//构造函数
        
        function 构造函数() {
            this.属性名 = 值,
            this.方法名 = function() {}
        }
```



###### 	属性和方法

调用属性和方法：obj.属性名（obj['属性名']）  /  obj.方法名

追加属性和方法：obj.属性名/方法名 = 值

遍历对象：for	in 循环





#### 4.ES6中类与对象

###### 	定义

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



###### 	继承（extends）

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





#### 5.ES6前的类

###### 	构造函数

```javascript
		function Star(name,age) {
            this.name = name;
            this.age = age
        }

		const ldh = new Star("刘德华",18)
```



###### 	prototype

js规定每一个构造函数都有一个prototype属性，该属性指向一个对象，这个对象的所有属性和方法都会被这个构造函数拥有



###### 

###### —proto—

每个对象都会有一个	—proto— 属性，该属性指向构造函数的prototype，所以实例对象才可以使用构造函数的prototype上的属性和方法



proto 为对象的查找机制提供了一条道路，不可以使用，只在内部指向prototype





###### 	constructor属性

proto和prototype中都有contractor属性，他指向构造函数本身，用于记录该对象引用了哪个构造函数



![image-20210803001056511](C:\Users\老韩头\AppData\Roaming\Typora\typora-user-images\image-20210803001056511.png)



###### 	



###### 原型链



![image-20210803001149679](C:\Users\老韩头\AppData\Roaming\Typora\typora-user-images\image-20210803001149679.png)



#### 6.ES6前的继承

方法：通过构造函数 + 原型   （借用call方法）

```javascript
		function.call(this,arg1,arg2,...) 	//this为当前函数调用时的this指向
```



1）借用构造函数继承父类属性

```javascript
		function Father(name,age) {
            this.name = name;
            this.age = age
        }

		function Son(name,age,sex) {
            Father.call(this,name,age);		//此时this指向Son的实例
            this.sex = sex
        }
```



2）借用原型对象prototype继承方法

```javascript
		Son.prototype = new Father()
		const son = new Son()
        //Son的实例son proto实际指向了Father的实例
```





#### 7.Date对象

```javascript
		//Date:构造函数	

		1.new Date()			//无参数返回当前时间
		2.new Date(2021,09,12)	//有参数则根据参数返回时间

		//时间戳	const date = new Date()
		1.date.valueOf() | date.getTime
		2.const date = +new Date()
        3.Date.now()
	
```





#### 8.数组

###### 	检测是否为数组

```
		Array.isArray(参数)
```



###### 	添加删除元素

```javascript
		arr.push(arg1,arg2,...)		//	向数组末添加 1或多 个元素
                 
        arr.pop()					//删除数组最后一个

		arr.unShift(arg1,arg2,...)	//	向数组开头添加 1或多 个元素
                    
        arr.shift()					//删除第一个
```



######  排序

```javascript
		arr.reverse()				//颠倒数组顺序

		arr.sort(callback)			//升（降）序排列
		
		//注意：sort无参数时，当数组中有两位或以上会失效
		//解决方案传入一个函数
		function(a,b) {
            return a - b	//升序
            return b - a	//降序
        }
```



###### 获取索引（查找元素）

```javascript
		arr.indexOf(searchValue,[index])			//返回指定元素的第一个索引 不存在则返回 -1 , index 规定开始检索的位置

		arr.lastIndexOf(searchValue,[index])

		arr.find( (value,index) => {})				//返回满足条件的第一个元素

		arr.findIndex( (value,index,arr) => {} )	//返回满足条件的第一个元素的索引

		arr.includes(参数)							//判断是否包含指定元素 返回true | false
```





###### 转化字符串

```javascript
		arr.toString()			  //返回一个字符串 每项用 ，隔开

		arr.join('分隔符')			//返回一个字符串 用 指定分隔符 隔开
```





###### 遍历

```javascript
		arr.forEach( (value,index,arr) => {})

		arr.filter( (value,index,arr) => {})		//该方法创建一个新数组 新数组是通过检查旧数组中符合的元素 用于筛选数组

		arr.some( (value,index,arr) => {})			//用于检测是否有满足条件的元素 返回true | false

		//区别 forEach和filter中的return 不会结束遍历，some中的会
		map()    erery()
```







#### 9.字符串

注：字符串为基本数据类型，但是有属性和方法

```javascript
		//基本包装类型
		const str = ***   ==>		cosnt temp = new String(***)
                                    str = temp	
                                    //销毁temp
```

当我们给str赋值时，数据不会被覆盖，会在内存中重新开辟一个空间，改变str指向



###### 获取指定字符索引

```javascript
		str.indexOf('指定字符',[开始的位置])		//返回索引号，未找到返回 -1

		str.lastIndexOf()					 
```





###### 获取指定位置字符

```javascript
		str.charAt(index)			//获取指定位置字符 与 str[index]等效

		str.charCodeAt(index)		//获取指定位置字符 ASCLL 码值
```





###### 截取拼接字符串

```javascript
		str.substr(startIndex,length)		//返回截取的字符

		str.subString(startIndex,endIndex)	//返回从 start 到 end-1 的字符串
```



###### 替换字符

```
		str.replace(regexp/substr,replacement)
```



###### 转化为数组

```javascript
		str.split('分隔符',[maxCount])		//分隔符要与字符间分隔符相同 若没有则为""  maxCount返回数组的最大长度
```





###### 其他

```javascript
		trim()			//清除两边空格
		
		repeat(n)		//将字符重复n遍 f
```

