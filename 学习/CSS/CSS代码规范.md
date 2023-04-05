## class 命名
避免过度任意的简写。.btn 代表 button，但是 .s 不能表达任何意思。
class 名称应当尽可能短，并且意义明确。
随着项目模块增多，防止因为不同页面或者组件中定义的 css 冲突，所以规范 css 语法也变得至关重要，推荐:BEM，分别代表着:**Block(块)、Element(元素)、Modifier(修饰符)**
> .user-info {} # user-info 是一个块，我理解是一个模块
> .user-info--feature {} # user-info--feature 是一个修饰符，用来表示这个块的不同状态
> .user-info__title{} # user-info__title 是一个元素，属于userinfo模块下的，多个元素组成块

```html
<div class="user-info">
  <div class="user-info__title">张三</div>
  <div class="user-info__age">18</div>
</div>
```

```html
<div class="tabs">
  <div class="tab tab-active">选中的标签</div>
  <div class="tab ">标签二</div>
  <div class="tab ">标签三</div>
</div>
```


## css 属性声明顺序
1. Positioning
2. Box model
3. Typographic
4. Visual
5. Misc
由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。
其他属性只是影响组件的 内部 或者是不影响前两组属性，因此排在后面。
```css
.declaration-order {
  /* Positioning  定位和层级等属性*/
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model 盒子模型或者浮动相关*/
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography 字体配置*/
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual 背景色边框等*/
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc 透明度和动画等*/
  opacity: 1;
  transition: all 0.5s;
}
```
