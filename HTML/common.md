# 一. 通用规范

规则前面加`*`为强制，不加为可选。

## \*Protocol
忽略图片，其他媒体类型文件，样式表和脚本的 URLs 中 `http` ，`https` 的协议头。

原因：针对 HTML 中的图片资源，引用的脚本资源来说，忽略资源的 HTTP 和 HTTPS 的协议头（仅限这两种协议）写成相对 URL 的形式（以//开头称为相对URL）则会根据当前的网页协议，自动在 `//` 前面加上相同的协议。

```html
<!-- Not recommended -->
<script src="https://www.google.com/js/gweb/analytics/autotrack.js"></script>
<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

## \*缩进
一次缩进四个空格，不要用 Tab 和空格混用

设置我们的开发工具，将一个 Tab 设置为四个空格，输入 Tab 时自动转换。

```html
<p>
□□□□<span>文本</span>
</p>
```

## \*大小写
HTML 元素名，属性，属性值，CSS选择器，属性和属性值均用小写

（注：此条规则针对原生标签，不适用自定义标签）

```html
<button class="u-btn" title="button">一个按钮</button>
```

## \*编码
以无 BOM 的 utf-8 编码作为文件格式

## \*文件类型
采用 HTML5

HTML5 中不要闭合空元素 `<br>` ，而不是 `<br />` ，这条规范是在 HTML 规范的演进中规定的

## \*语义化
正确的地方使用正确的元素，合理使用 HTML 元素

- 利于 SEO
- 当网页没有完成加载 CSS 的时候，也会有良好的布局
- 阅读屏幕阅读器能够识别语义化的标签
- 对我们写标准的标签是一种好习惯

标签                                | 语义
---------------------------------   |---
&lt;p&gt;                           | 段落
&lt;h1&gt; &lt;h2&gt; &lt;h3&gt;... | 标题
&lt;ul&gt;                          | 无序列表
&lt;ol&gt;                          | 有序列表
......                              | ......


## \*多媒体后备方案
为图片加上 `alt` 属性，为视频，音频加上视频字幕和文字标题说明，其他多媒体同理，便于屏幕阅读器识别。

```html
<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
```

## \*关注点分离
结构（HTML），表现（CSS），行为（JavaScript）分离，**尽量** 使耦合达到最低。

## \*实体引用
不要随意使用实体引用，除了特殊含义的字符外。

特殊含义的字符有："<", ">", "不间断空格（non-breaking space）"

## \*类型属性
HTML5 中忽略样式表和脚本的 `type` 属性

```html
<link rel="stylesheet" href="//www.google.com/css/maia.css">
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

## \*通用格式化
结构书写中，块、列表、表格元素均应单独成行，他们的子元素也必须缩进。

除非单独成行会影响样式外，比如 `<li>` 元素，应该具体情况具体分析。

```html
<blockquote>
  <p><em>Space</em>, the final frontier.</p>
</blockquote>
<ul>
  <li>Moe</li>
  <li>Larry</li>
  <li>Curly</li>
</ul>
<ul>
  <li>Moe</li>
  <li>Larry</li>
  <li>Curly</li>
</ul>
<table>
  <thead>
    <tr>
      <th scope="col">Income</th>
      <th scope="col">Taxes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$ 5.00</td>
      <td>$ 4.50</td>
    </tr>
  </tbody>
</table>
```

## \*其他
- CSS 在 `head` 里外链，JS 在 `body` 底外链；
- 在满足语义和视觉的基础上，尽可能简化结构，不要有冗余的结构；
- 多采用 HTML5 新标签，尤其是 WAP 页开发；
