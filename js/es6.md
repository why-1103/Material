# let 和 const 命令
## let 命令 
1. 所声明的变量，只在let命令所在的代码块内有效。
2. 不存在变量提升，存在暂时性死区，所声明的变量一定要在声明后使用，否则报错。
3. 不允许在相同作用域内，重复声明同一个变量

	>es6新增块级作用域,允许任意嵌套

## const命令
1. 声明一个只读的常量。一旦声明，常量的值就不能改变。
2. 一旦声明变量，就必须立即初始化，不能留到以后赋值。
3. 不存在变量提升，存在暂时性死区，只能在声明的位置后面使用。
4. 对于复合类型的数据（主要是对象和数组），保持指针固定
5. 对象冻结，使用Object.freeze方法


特性：let命令、const命令、class命令声明的全局变量，不属于顶层对象(windows)的属性。

## 顶层对象

- 浏览器里面，顶层对象是window，但 Node 和 Web Worker 没window。
- 浏览器和 Web Worker 里面，self也指向顶层对象，但是 Node没有self。
- Node 里面，顶层对象是global，但其他环境都不支持。

### this局限性
- 全局环境中，this会返回顶层对象。但是，Node 模块和 ES6 块中，this返回的是当前模块。
- 函数里面的this，如果函数不是作为对象的方法运行，而是单作为函数运行，this会指向顶层对象。但是，严格模式下，这this会返回undefined。
- 不管是严格模式，还是普通模式，new Function('returnthis')()，总是会返回全局对象。但是，如果浏览器用了 CS（Content Security Policy，内容安全策略），那么eval、newFunction这些方法都可能无法使用。
 
```
	// 方法一
	(typeof window !== 'undefined'? window : (typeof process === 'object' && typeof require === 'function' && typeof global === 'object')
     ? global
     : this);

	// 方法二
	var getGlobal = function () {
  		if (typeof self !== 'undefined') { return self; }
  		if (typ’’’eof window !== 'undefined') { return window; }
  		if (typeof global !== 'undefined') { return global; }
  	throw new Error('unable to locate global object');
	};
```

# 变量的解构赋值
## 数组的解构赋值
	“模式匹配”，只要等号两边的模式相同，左边的变量就会被赋予对应的值。
1. 普通数组：
 	let [a, b, c] = [1, 2, 3];
2. 嵌套数组：
	1. let [foo, [[bar], baz]] = [1, [[2], 3]];
	2. let [x, , y] = [1, 2, 3];
	3. let [head, ...tail] = [1, 2, 3, 4];
	4. let [x, y, ...z] = ['a'];
## 对象的解构赋值 
	let { foo, bar } = { foo: 'aaa', bar: 'bbb' };
	对象的属性没有次序，变量必须与属性同名，才能取到正确的值。
	let obj = {
  p: [
    'Hello',
    { y: 'World' }
   ]
  };

 let { p: [x, { y }] } = obj;
	
	对象的解构也可以指定默认值。默认值生效的条件是，对象的属性值严格(===)等于undefined
##字符串的解构赋值
``` js
const [a, b, c, d, e] = 'hello';
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"
	
let {length : len} = 'hello';
len // 5
```
## 变量解构赋值用途
1. 交换变量的值：[x, y] = [y, x];
2. 从函数返回多个值
3. 函数参数的定义([数组传参],{对象传参})
4. 提取 JSON 数据
5. 遍历 Map 结构