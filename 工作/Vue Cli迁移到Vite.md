官方教程：
[How to Migrate from Vue CLI to Vite - Vue School Articles](https://vueschool.io/articles/vuejs-tutorials/how-to-migrate-from-vue-cli-to-vite/)
vite不支持~（作用类似于@）
```js
换成相对路径
```
vite不支持require
```js
可以用插件，但不好用
```
vite不支持require.context(用于一次性引入多个)
```js
require.context 改成 import.meta.globEager
```
