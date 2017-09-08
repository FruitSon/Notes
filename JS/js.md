#JavaScript

####ECMAScript -> Javascript
JS是符合ECMA语言标准的一种实现

```Javascript
<html>
<head></head>
<body>...</body>
</html>
```

####JS代码可以直接嵌入（一般在`<head>`),或者通过引入单独的`.js`文件
```Javascript
<head> <script></script></head>
OR
<head><script src="..."></script></head>
```
####Case-sensitive

##基本语法
####数据类型
- Number  
	不区分整型与浮点型  
	NaN:not a number,当无法计算结果时用NaN表示  
	`NaN`与任何值都不相等，包括自己。判断`NaN`用`isNaN()`，但`isNaN()`放入非Number类型返回`true`
	浮点数的比较需要通过**检查其差的绝对值是否小于阈限**。不能直接比较，因为无法精确表示循环小数。 
```Javascript
	NaN === NaN; // false
	isNaN(NaN); //true
	1/3 === (1- 2/3); //false
	Math.abs(1 / 3 - (1 - 2 / 3)) < 0.0000001; // true

```
- String  
	多行字符串 1.`\n` 2.反引号`` ... `  `(ES6)
	```Javascript
	alert(`多行
	字符串
	测试`);
	```
	模板字符串(ES6)
	```Javascript
	var name = '小明';
	var age = 20;
	var message = `你好, ${name}, 你今年${age}岁了!`;
	```
	字符串操作
	```Javascript
	var s = 'Hello, world!';
	s.length; // return length: 13
	s[1]; //return char on position 1: 'e'
	s[13]; //return char on position 13: 超出索引返回undefined
	s.toUpperCase(); // 'HELLO, WORLD!'
	s.toLowerCase();
	s.indexOf('world'); // search the idx of target substring
	s.indexOf('World'); // return -1 if can't find the target substring
	s.substring(0, 5); // return substring from 0 (included) to 5 (excluded): 'Hello'
	s.substring(7); // return substring from 7 (included) to end: 'world'
	```

- Boolean

####比较运算符 
**JS里允许对任意数据类型进行比较**  
	`==`:比较时自动转换数据类型  
	`===`:比较同一数据类型的值。如果数据类型不一致返回false   
	`null`&`undefined`：`null`表示‘空’的值。（JS是弱类型所以null与其他类型的空值比较也会是false?)；`undefined`表示未定义，一般用在判断**函数是否成功传参**
```Javascript
	false == 0; // true    
	false === 0; // false 
	null === undefined //false
	null == undefined //true

```
####Array
直接给`Array`的`length`赋值会引起`Array`大小的变化  
如果通过索引赋值时超过了范围，同样会引起Array大小的变化
```Javascript
var arr1 = [1, 3.14, 'Hello', null, true];
var arr2 = new Array(1, 3.14, 'Hello', null, true);

arr1.length; //5
arr1.length = 3;
arr1; //[1, 3.14, 'Hello']

arr2[6] = 'append';
arr2; //[1, 3.14, 'Hello', null, true, undefined, 'append']

```
Array操作
```Javascript
arr = [1, 3.14, 'Hello', true]
arr.indexOf(1); //search the position of a specific element: 0
arr.slice(1,3); //sub-array: [3.14, 'Hello']
arr.slice(1);	//sub-array: [3.14, 'Hello', true]
arr.slice();	//copy: [1, 3.14, 'Hello', true] //但是arrCopy ==(=) arr //false

arr.push('p1','p2');		//add element on the end of array
arr.pop();		//delete element on the end of array, return the removed element: 'p2'
arr.pop()*5;	//applying pop() on the empty array returns undefined

arr.unshift('s1');	//add element on the beginning of array
arr.shift();		//delete element on the beginning of array
arr.shift();		//applying shift on the empty array returns undefined

arr.sort();
arr.reverse();

//splice()从指定的索引开始删除若干元素，然后再从该位置添加若干元素
as = ['a','b','c','d'];
as.splice(1, 2);				   // 删除: 从idx = 1 (included)的地方开始删除2个元素, return the deleted items ['b','c'] 
as;								//['a','d']

as = ['a','b','c','d'];
as.splice(1, 2, 'bbb', 'ccc'); 	// 删除再添加'bbb','ccc'
as;								//['a','bbb','ccc','d']

as = ['a','b','c','d'];
as.splice(1,0,'bbb','ccc');		// 添加: 在idx之后添加'bbb','ccc'
as;								//['a', 'b', 'bbb', 'ccc', 'c','d']


```


####Object
包括许多key-value的无序集合
```Javascript
var person = {
    name: 'Bob',
    age: 20,
    tags: ['js', 'web', 'mobile'],
    hasCar: true,
    zipcode: null
};

person.name; //access value
```
####变量
JS中同一个变量可以反复赋值（包括不同类型的）->动态语言
- const:常量
- let:变量。块作用域，不能重复声明覆盖
- var:变量。函数作用域，能重复声明覆盖 *不用`var`申明的变量是全局变量*    
—>`'use strict'`;  //在stric模式中运行，强制通过`var`申明变量

