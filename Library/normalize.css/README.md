# normalize.css

<a href="https://github.com/necolas/normalize.css"><img
  src="https://necolas.github.io/normalize.css/logo.svg" alt="Normalize Logo"
  width="80" height="80" align="right"></a>

> CSS 重置的现代替代品

[![npm][npm-image]][npm-url] [![license][license-image]][license-url]
[![changelog][changelog-image]][changelog-url]
[![gitter][gitter-image]][gitter-url]


**NPM**

```sh
npm install --save normalize.css
```

**Bower**

```sh
bower install --save normalize-css
```

**CDN**

参见 https://cdnjs.com/libraries/normalize

**Download**

参见 https://necolas.github.io/normalize.css/latest/normalize.css


## 它能做什么?

  * 与许多 CSS 重置不同，它保留有用的默认值
  * 对各种元素的样式进行规范化
  * 纠正错误和常见的浏览器不一致
  * 通过细微的修改提高可用性
  * 注释详细，阐明代码如何使用


## Browser support

* Chrome (last two)
* Edge (last two)
* Firefox (last two)
* Firefox ESR
* Internet Explorer 8+
* iOS Safari (last two)
* Opera (last two)
* Safari 6+
* _[Normalize.css v1 提供遗留的浏览器支持](https://github.com/necolas/normalize.css/tree/v1) (IE 6+, Safari 4+), 但不再积极开发._



## 扩展的细节和已知的问题

关于 normalize.css 的难懂部分的更多细节和解释
Additional detail and explanation of the esoteric parts of normalize.css.

#### `pre, code, kbd, samp`

`font-family: monospace, monospace` hack 修复了用于格式化文化的 font-size 的继承和扩展。
`monospace` 的重复是有意为之。
[Source](https://en.wikipedia.org/wiki/User:Davidgothberg/Test59).

#### `sub, sup`

正常情况下，使用  `sub` 或 `sup` 会影响所有浏览器的文本框高度。
[Source](https://gist.github.com/413930).

#### `svg:not(:root)`

添加 `overflow: hidden` 修复了 IE9 的 SVG 渲染。
更早版本的 IE 不支持 SVG，因此我们可以安全地使用 `:not()` 和 `:root`选择器，
现代浏览器使用默认的 UA 样式表来应用这种样式。
[Source](https://lists.w3.org/Archives/Public/public-svg-wg/2008JulSep/0339.html).

#### `select`

默认情况下，OS X 上的 Chrome 和 OS X 上的 Safari 允许 `select` 的非常有限的样式
，除非设置了 border 属性。
`optgroup` 元素的默认 font weight 在 OS X 的 Chrome 和 OS X 上的 Safari 上，元素不能被安全地改变。

#### `[type="checkbox"]`

建议您不要为复选框和单选输入框添加样式，因为 Firefox 的实现不尊重 box-sizing、padding 或 width。

#### `[type="number"]`

特定的字体大小值被应用于数字输入，导致递减按钮的光标样式从 `default` 更改为 `text`。

#### `[type="search"]`

默认情况下，搜索框并不是完全可样式化的。
在 OSX/iOS 上的 Chrome 和 Safari 中，你无法控制 `font`、`padding`、`border` 或 `background`。
在 Chrome 和 Safari 浏览器上，你不能正确地控制 `border`。
它将应用 `border-width`，但只显示边界的边界颜色(无法控制)。
应用 `-webkit-appearance: textfield` 解决了这些问题而不移除搜索框的好处(例如显示过去的搜索)。Safari (而不是 Chrome)将在它有填充(和 `textfield` 外观)的时候对取消按钮进行裁剪。

## 贡献

请阅读[贡献指南](CONTRIBUTING.md)，以使每个人的贡献过程变得容易和有效。


[changelog-image]: https://img.shields.io/badge/changelog-md-blue.svg?style=flat-square
[changelog-url]: CHANGELOG.md
[license-image]: https://img.shields.io/npm/l/normalize.css.svg?style=flat-square
[license-url]: LICENSE.md
[npm-image]: https://img.shields.io/npm/v/normalize.css.svg?style=flat-square
[npm-url]: https://www.npmjs.com/package/normalize.css
[gitter-image]: https://img.shields.io/badge/chat-gitter-blue.svg?style=flat-square
[gitter-url]: https://gitter.im/necolas/normalize.css
