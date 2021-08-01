# JS

#### 	1.隐式转换

代表空或否定的值会被转化成false，其余为true

```javascript
			"" , NaN , 0 , undefined , null
```



###### 		对象与布尔值比较：

​		比较时，对象会先转化为字符串，然后再转化为数字

```javascript
		[] = true // false    []转化为'',然后转化为数字0, true转化为数字1
```

