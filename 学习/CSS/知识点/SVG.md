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
SVG 文件可通过以下标签嵌入 HTML 文档：<embed>、<object> 或者 <iframe>。
SVG的代码可以直接嵌入到HTML页面中，或您可以直接链接到SVG文件。

```html
<embed src="circle1.svg" type="image/svg+xml" />
```
