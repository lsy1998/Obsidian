## 介绍
@property是一个新增的CSS @规则(CSS at-rule)，它是[CSS Houdini](https://link.zhihu.com/?target=https%3A//developer.mozilla.org/en-US/docs/Web/Guide/Houdini) API的一部分, 它允许开发者显式地定义css自定义属性，并允许进行属性类型检查、设定默认值以及定义该自定义属性是否可以被继承。@property可以直接在样式表中注册自定义属性，无需运行任何JS代码；同时也配备相应的JS语法注册自定义属性。@property自定义属性，是CSS变量(CSS variables)声明变量的升级版本，比CSS变量更加规范和严谨。

## 基础语法规则
```css
@property <custom-property-name> {
  <declaration-list>
}
```
### declaration-list
声明字段包括 syntax 、inherits 和 initial-value
1. **syntax** ：类型string。定义自定义属性的类型。例如，number，color，percentage等
2. **inherits**：类型boolean。定义自定义属性是否允许继承
3. **initial-value**：类型符合 syntax 定义的类型，定义初始值
4. **syntax** 和 **inherits** 描述符是必需的，其中任何一项缺失, 整条规则都将失效并且会被忽略
5. **initial-value** 描述符仅在 syntax 描述符为通用syntax定义时是可选的，否则也是必需的

### syntax 可用有效字段
注册自定义属性时，可以使用CSS值和单位规范中的许多受支持的语法 - < length > - < number > - < percentage > - < length-percentage > - < color > - < image > - < url > - < integer > - < angle > - < time > - < resolution > - < transform-list > - < transform-function > - < custom-ident > (a custom identifier string)

### 例子
```css
@property --primary-color {
  syntax: '<color>';
  inherits: false;
  initial-value: green;
}

:root{
    --primary-color: blue;
}

.box {
    background-color: var(--primary-color);
}
```

## 参考资料
[一起了解一下css新特性@property - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/409933240)