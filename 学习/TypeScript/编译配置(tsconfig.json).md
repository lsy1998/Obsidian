## include
需要编译的文件
```js
**  //表示任意目录
* //表示任意文件
```
## exclude
不需要的文件
## compilerOptions
编译器选项
### target
### lib
### module
使用的模块系统
### outDir
编译后产生的文件所在的目录
### outFile
编译到一个文件里面
### allowJs
是否对js进行编译
### checkJs
检查js是否符合规范
### removeComments
是否移除注释
### noEmit
不生成编译后的文件
### noEmitOnError
有错误时不编译
### alwaysStrict
编译后的文件是否使用严格模式，默认false
### noImplicitAny
不允许隐式的any
### noImplicitThis
不允许不明确类型的this
### strictNullChecks
严格的检查空值
### strict
所有严格检查的总开关