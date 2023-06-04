

> ...

在JavaScript中，省略号(…)表示剩余参数语法，可以将多个参数表示为数组。例如：

```js
function myFunction(a, b, ...args) {   
	console.log(args); 
} 
myFunction(1, 2, 3, 4, 5);
```


这将输出：[3, 4, 5]