# TS注解

原始数据类型（==string，number,boolean==）默认可以为 null，undefined，symbol

#### 	

#### 	object类型

泛指指非基础类型

```tsx
		const foo:object = {} || [] || function(){} 
        cosnt foo:{} = {}
```

#### 	array类型

```tsx
 		const arr1:<number> = [1,2,3] 
 		const arr2:number[] = [1,23,3]
```

==元组类型==：明确元素数量和元素类型的数组

#### 	enum类型（枚举）

```tsx
		enum *** {NO = 0 , YES = 1}   //可以不用赋值 TS枚举默认从0开始递增
```

#### 	function类型

```tsx
		function(num1:number,num2:string):string{	//参数()后:string 对函数输出做限制
            return "hello"
        }		
```

#### 	any类型



#### 	类型断言

1.使用as

```tsx
		const num1 = res as number
```

2.<>方式

```tsx
		const num2 = <number>res	//在react中 可能会与jsx下的标签产生冲突
```



#### 	interfaces 接口

​	用于限制对象

```tsx
		interfaces *** {
            title:string,
            content:string,
            subTitle?:string,
            readonly sumary:string	//若有其他修饰符 readyonly要写在后面
        }
		
		//不固定的键值
		interfaces *** {
           [key]:string:string
        }
		
```



#### 类

类的访问修饰符 public private protected private protected都不能在外部被访问 protected可以在子类中访问

类的只读属性 readyonly 若是属性已经有了修饰符 readyOnly要写在其后面

