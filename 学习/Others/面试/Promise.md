## Promise
promise 是处理异步请求的特殊对象

## 状态
Promise 有三种状态。
1. **pending**(进行中): 初始状态，不是成功或失败状态。处于 pending 状态时，可以使用 then() 方法指定成功和失败的回调函数，**then()方法中的回调函数会统一处理fulfilled和rejected，而不是单独为这两种状态指定不同的处理函数**。
2. **fulfilled**(已完成): 意味着操作成功完成。已经处于 fulfilled 或 rejected 状态，将立即执行相应的回调函数。
3. **rejected**(已失败): 意味着操作失败。已经处于 fulfilled 或 rejected 状态，将立即执行相应的回调函数。

#### 示例

```js
function getData(url) {  
  return new Promise((resolve, reject) => {  
    const xhr = new XMLHttpRequest();  
    xhr.open("GET", url);  
    xhr.onload = () => {  
      if (xhr.status === 200) {  
        resolve(xhr.responseText);  
      } else {  
        reject(new Error(xhr.statusText));  
      }  
    };  
    xhr.onerror = () => reject(new Error("Network Error"));  
    xhr.send();  
  });  
}  
  
getData("https://example.com/todos/1")  
  .then((data) => console.log(data))  
  .catch((error) => console.error(error));
```

## 知识点
#### await
await会让返回的promise变成直接返回promise的resolve或reject的值
#### then
then方法是Promise对象的一个方法，它可以接受两个参数，分别是onFulfilled和onRejected。onFulfilled是一个函数，它会在Promise状态变为fulfilled时被调用，onRejected是一个函数，它会在Promise状态变为rejected时被调用。如果你只传递了onFulfilled参数，那么then方法只有在Promise状态变为fulfilled时才会被调用。如果你想在Promise状态变为rejected时也有相应的处理，你可以传递第二个参数onRejected，或者使用catch方法。
#### catch
catch方法是then方法的一种简写形式，它相当于then(undefined, onRejected)。  catch方法返回的是一个新的Promise对象，它可以继续链式调用then方法。如果catch方法没有抛出异常或返回一个被拒绝的Promise对象，那么它返回的Promise对象会被兑现（fulfilled）。
#### then和catch
catch方法可以捕获前面then方法中抛出的异常，而then方法的第二个参数不能捕获自身的异常。
