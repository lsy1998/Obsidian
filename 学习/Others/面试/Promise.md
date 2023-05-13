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
await是一个运算符，用于等待一个表达式的结果，它只能在异步函数（async function）中使用。
await可以等待一个Promise对象，也可以等待一个普通的值。如果等待的是一个Promise对象，await会阻塞后面的代码，直到Promise对象被兑现（resolve）或拒绝（reject），并返回其兑现的值或抛出拒绝的原因。如果等待的是一个普通的值，await会直接返回该值。
await可以用于等待异步函数的返回值，也可以用于等待其他的异步操作，比如setTimeout，fetch等。
#### then
then方法是Promise对象的一个方法，它可以接受两个参数，分别是onFulfilled和onRejected。onFulfilled是一个函数，它会在Promise状态变为fulfilled时被调用，onRejected是一个函数，它会在Promise状态变为rejected时被调用。如果你只传递了onFulfilled参数，那么then方法只有在Promise状态变为fulfilled时才会被调用。如果你想在Promise状态变为rejected时也有相应的处理，你可以传递第二个参数onRejected，或者使用catch方法。
#### catch
catch方法是then方法的一种简写形式，它相当于then(undefined, onRejected)。  catch方法返回的是一个新的Promise对象，它可以继续链式调用then方法。如果catch方法没有抛出异常或返回一个被拒绝的Promise对象，那么它返回的Promise对象会被兑现（fulfilled）。
#### then和catch
catch方法可以捕获前面then方法中抛出的异常，而then方法的第二个参数不能捕获自身的异常。

## Some Questions 
#### promise不管包装的是什么内容都会是异步的吗?

答：
•  promise是一种用于表示异步操作的最终完成或失败及其结果值的对象。
•  promise可以包装任何类型的值，无论是普通的值还是另一个promise对象。
•  promise本身并不是异步的，它只是一个代理，用于在未来某个时候把值交给使用者。
•  promise的异步性体现在它的状态转换上，它有三种状态：待定（pending），已兑现（fulfilled）和已拒绝（rejected）。
•  当一个promise被创建时，它处于待定状态，此时它还没有被兑现或被拒绝，也没有任何结果值。
•  当一个promise被兑现或被拒绝时，它就变成了已敲定（settled）状态，此时它有一个不可变的结果值，并且不能再改变状态。
•  promise的状态转换通常是由异步操作触发的，比如setTimeout，fetch等。当异步操作完成时，它会调用promise构造函数中传入的resolve或reject函数，从而改变promise的状态，并传递结果值。例如：

```js
const myPromise = new Promise((resolve, reject) => {
setTimeout(() => {
resolve("foo"); // 异步操作完成后，调用resolve函数，将promise状态从pending变为fulfilled，并传递结果值'foo'
}, 300);
});
```

•  promise的状态转换也可以由同步操作触发，比如直接在构造函数中调用resolve或reject函数。例如：

```js
const myPromise = new Promise((resolve, reject) => {
resolve("bar"); // 同步操作完成后，调用resolve函数，将promise状态从pending变为fulfilled，并传递结果值'bar'
});
```

•  但是，即使promise的状态转换是由同步操作触发的，它也不会立即执行与之关联的处理函数（then，catch等），而是会将它们放入微任务队列（microtask queue），等待当前执行栈清空后再执行。这样做的目的是为了保证promise的行为一致性和可预测性。例如：

```js
const myPromise = new Promise((resolve, reject) => {
resolve("bar"); // 同步操作完成后，调用resolve函数，将promise状态从pending变为fulfilled，并传递结果值'bar'
});
myPromise.then((value) => {
console.log(value); // 这个函数不会立即执行，而是会放入微任务队列中等待
});
console.log("baz"); // 这个语句会先于上面的函数执行
// 输出：
// baz
// bar
```

•  因此，可以说**promise不管包装的是什么内容都会有一定程度的异步性，但这并不意味着它们都会产生新的异步操作。这取决于promise内部如何触发状态转换和结果值传递**。