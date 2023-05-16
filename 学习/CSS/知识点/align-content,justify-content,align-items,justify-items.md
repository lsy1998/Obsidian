![[Pasted image 20230404194422.png]]
## align-items

## Some Questions

#### align-items 既能控制 flex 布局又能控制 grid 布局的对齐方向吗?

**答**：是的，align-items 属性可以用于 flex 布局和 grid 布局，它们的作用是类似的，都是用来控制容器中的项目在交叉轴方向上的对齐方式。不过，它们也有一些区别，比如：

•  在 flex 布局中，交叉轴是与主轴垂直的轴，它的方向取决于 flex-direction 的值。在 grid 布局中，交叉轴是与网格行平行的轴，它的方向取决于 writing-mode 和 direction 的值。

•  在 flex 布局中，align-items 只能对齐单行或单列的 flex 项目，如果要对齐多行或多列的 flex 项目，需要使用 align-content 属性。在 grid 布局中，align-items 可以对齐任意数量的网格项，不需要使用 align-content 属性。

•  在 flex 布局中，align-items 的默认值是 stretch ，在 grid 布局中，align-items 的默认值是 normal 

#### 什么是交叉轴？

**答**：交叉轴是与主轴垂直的轴，它的方向取决于主轴的方向。在 flex 布局和 grid 布局中，交叉轴可以用来控制容器中的项目在垂直于主轴的方向上的对齐方式。(developer.mozilla.org)(developer.mozilla.org)

在 flex 布局中，如果主轴是水平方向（flex-direction: row 或 row-reverse），那么交叉轴就是从上至下地垂直走向的。如果主轴是垂直方向（flex-direction: column 或 column-reverse），那么交叉轴就是水平走向的。(developer.mozilla.org)(developer.mozilla.org)

在 grid 布局中，交叉轴是与网格行平行的轴，它的方向取决于 writing-mode 和 direction 的值。