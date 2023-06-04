Function.prototype.bind() bind() 方法创建一个新的函数，在 bind() 被调用时，这个新函数的 this 被指定为 bind() 的第一个参数，而其余参数将作为新函数的参数，供调用时使用。

```js
    var hello = function (a, b, c, d) {
      console.log(this.temp);
      console.log(a, b, c, d)
    };

    var demo = {
      name: 'demo'
    };

    var h = hello.bind(demo, 1, 2);
    h(3, 4); // out 'demo' '1 2 3 4 '
    
```

可以看出，bind方法实现了更改原函数内部的this指向并返回了一个新函数出来。所以后面要有一个小括号，也就是执行后才会得到对应的结果。bind中里第一个括号里面的第一个参数被当做函数的this，其余参数包括后面执行函数时传入的参数依次被原函数使用（[[柯里化]]）。