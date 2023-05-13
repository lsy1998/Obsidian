## Promise
promise 是处理异步请求的特殊对象

## 状态
Promise 有三种状态。
1. **pending**(进行中): 初始状态，不是成功或失败状态。处于 pending 状态时，可以使用 then() 方法指定成功和失败的回调函数。
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
