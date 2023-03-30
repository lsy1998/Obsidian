## 什么是SVG
**SVG（Scalable Vector Graphics）是一种基于 XML 的标记语言，用于描述二维矢量图形**。简单地说，<font color="#76923c">SVG 之于图像就像 HTML 之于文本</font>。顾名思义，与光栅图像（JPG、GIF 和 PNG）不同，SVG 允许您在不损失图像质量的情况下任意放大或缩小矢量图像。
> -   SVG 指可伸缩矢量图形 (Scalable Vector Graphics)
> -   SVG 用来定义用于网络的基于矢量的图形
> -   SVG 使用 XML 格式定义图形
> -   SVG 图像在放大或改变尺寸的情况下其图形质量不会有所损失
> -   SVG 是万维网联盟的标准
> -   SVG 与诸如 DOM 和 XSL 之类的 W3C 标准是一个整体

---

## 优势
> -   SVG 可被非常多的工具读取和修改（比如记事本）
> -   SVG 与 JPEG 和 GIF 图像比起来，尺寸更小，且可压缩性更强。
> -   SVG 是可伸缩的
> -   SVG 图像可在任何的分辨率下被高质量地打印
> -   SVG 可在图像质量不下降的情况下被放大
> -   SVG 图像中的文本是可选的，同时也是可搜索的（很适合制作地图）
> -   SVG 可以与 JavaScript 技术一起运行
> -   SVG 是开放的标准
> -   SVG 文件是纯粹的 XML

---
## svg在html中
通过以下标签嵌入 HTML 文档：`<embed>`、`<object>` 或者 `<iframe>`
也可以直接嵌入到HTML页面中，或您可以直接链接到SVG文件
```html
<embed src="circle1.svg" type="image/svg+xml" />
```

```html
<object data="circle1.svg" type="image/svg+xml"></object>
```

```html
<iframe src="circle1.svg"></iframe>
```

```html
<svg xmlns="http://www.w3.org/2000/svg" version="1.1"> <circle cx="100" cy="50" r="40" stroke="black" stroke-width="2" fill="red" /> </svg>
```

```html
<a href="circle1.svg">查看 SVG 文件</a>
```

## SVG矩形
`<rect>` 标签可用来创建矩形，以及矩形的变种
```html
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">  
  <rect width="300" height="100"  
  style="fill:rgb(0,0,255);stroke-width:1;stroke:rgb(0,0,0)"/>  
</svg>
```
> -   rect 元素的 width 和 height 属性可定义矩形的高度和宽度
> -   style 属性用来定义 CSS 属性
> -   CSS 的 fill 属性定义矩形的填充颜色（rgb 值、颜色名或者十六进制值）
> -   CSS 的 stroke-width 属性定义矩形边框的宽度
> -   CSS 的 stroke 属性定义矩形边框的颜色
```html
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">  
  <rect x="50" y="20" width="150" height="150"  
  style="fill:blue; stroke :pink;stroke-width:5;fill-opacity:0.1;  
  stroke-opacity:0.9"/>  
</svg>
```
> -   x 属性定义矩形的左侧位置（例如，x="0" 定义矩形到浏览器窗口左侧的距离是 0px）
> -   y 属性定义矩形的顶端位置（例如，y="0" 定义矩形到浏览器窗口顶端的距离是 0px）
> -   CSS 的 fill-opacity 属性定义填充颜色透明度（合法的范围是：0 - 1）
> -   CSS 的 stroke-opacity 属性定义轮廓颜色的透明度（合法的范围是：0 - 1）
```html
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">  
  <rect x="50" y="20" width="150" height="150"  
  style="fill:blue; stroke :pink;stroke-width:5;opacity:0.5"/>  
</svg>
```
> -   CSS opacity 属性用于定义了元素的透明值 (范围: 0 到 1)。
```html
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">  
  <rect x="50" y="20" rx="20" ry="20" width="150" height="150"  
  style="fill:red; stroke :black;stroke-width:5;opacity:0.5"/>  
</svg>
```
> -   rx 和 ry 属性可使矩形产生圆角。
