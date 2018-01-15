<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# CSS Modules

一个 **CSS Module** 是一个 CSS 文件，其中所有类名称和动画名称默认在本地作用域内。
所有的 URL (`url(...)`) 和 `@import` 都是模块请求格式（`./xxx` 和 `../xxx` 表示相对路径，`xxx` 和 `xxx/yyy` 表示模块文件夹中，即 `node_modules`）。


CSS Modules 编译为一个名为 ICSS 或 [Interoprable CSS](https://github.com/css-modules/icss) 的低阶交换格式，但是像普通的 CSS 文件一样进行书写：

``` css
/* style.css */
.className {
  color: green;
}
```

当从 JS 模块导入 **CSS Module** 时，它导出一个对象，其中包含从本地名称到全局名称的所有映射。

``` js
import styles from "./style.css";
// import { className } from "./style.css";

element.innerHTML = '<div class="' + styles.className + '">';
```

## 命名

对于本地的类名，推荐使用驼峰式命名，但不是强制的。

> **[info]** 这是推荐的，因为当尝试以点符号访问 style.class-name 时，常见的替代方法 kebab-casing 可能会导致意外的行为。你仍然可以使用括号符号（例如`style['class-name']`）来处理 kebab-case，但是 `style.className` 更清晰。

## 例外


`:global` 切换当前选择器相应标识符的到全局作用域。`:global(.xxx)` 各自的 `@keyframes :global(xxx)` 在全局作用域内的括号中声明了这些东西。

同样，局部作用域的 `:local` 和 `:local(...)`。

如果选择器切换到全局模式，规则的全局模式也会被激活。（这使我们可以使 `animation: abc;` 本地化。）

例如：`.localA :global .global-b .global-c :local(.localD.localE) .global-d`

## 组合

组合选择器是可以的:

``` css
.className {
  color: green;
  background: red;
}

.otherClassName {
  composes: className;
  color: yellow;
}
```

可以有多个 `composes` 规则，但是 `composes` 规则必须在其他规则之前。 扩展只对局部作用域的选择器工作，并且只在选择器是一个单个类名的情况下。 当一个类名组合另一个类名时，**CSS Module** 将同时导出本地类的两个类名。组合可以添加多个类名称。

可以组合多个类：`composes: classNameA classNameB;`。

## 依赖

### 组合其他文件

可以组合来自其他 **CSS Modules** 的类名：

``` css
.otherClassName {
  composes: className from "./style.css";
}
```

注意，在从不同的文件组合多个类时，应用的顺序是*未定义*的。
当在一个单一类中组合不同的文件时，请确保不要为多个类名中的相同属性定义不同的值。

注意，组合不应该形成一个循环依赖。否则，一个规则的属性是否覆盖一个组合规则的属性是*未定义*的。模块系统可能会发出错误。

如果类只做一件事，而依赖关系是层次化的，那么最好。

### 组合全局类名

可以组合来自 **global** 类名：

```css
.otherClassName {
  composes: globalClassName from global;
}
```

## 使用预处理器

预处理器可以很容易地定义块全局或局部。

即使用 less.js

``` less
:global {
  .global-class-name {
    color: green;
  }
}
```

## Why?

**模块化的** 和 **可重用的** CSS!

* 没有更多的冲突。
* 显式的依赖关系。
* 没有全球作用域。

## 示例

* [css-modules/webpack-demo](https://github.com/css-modules/webpack-demo)
* [outpunk/postcss-modules-example](https://github.com/outpunk/postcss-modules-example)
* [Theming](docs/theming.md)
* [css-modules/browserify-demo](https://github.com/css-modules/browserify-demo)
* [x-team/starting-css-modules](https://github.com/x-team/starting-css-modules)

## 历史

* 04/2015: `placeholders` feature in css-loader (webpack) allows local scoped selectors (later renamed to `local scope`) by @sokra
* 05/2015: `postcss-local-scope` enables `local scope` by default (see [blog post](https://medium.com/seek-ui-engineering/the-end-of-global-css-90d2a4a06284)) by @markdalgleish
* 05/2015: `extends` feature in css-loader allow to compose local or imported class names by @sokra
* 05/2015: First CSS Modules spec document and github organization with @sokra, @markdalgleish and @geelen
* 06/2015: `extends` renamed to `composes`
* 06/2015: PostCSS transformations to transform CSS Modules into an intermediate format (ICSS)
* 06/2015: Spec for ICSS as common implementation format for multiple module systems by @geelen
* 06/2015: Implementation for jspm by @geelen and @guybedford
* 06/2015: Implementation for browserify by @joshwnj, @joshgillies and @markdalgleish
* 06/2015: webpack's css-loader implementation  updated to latest spec by @sokra


## 实现

### webpack

在模块模式下，Webpack的 [css-loader](https://github.com/webpack/css-loader) 用全局唯一名称（默认情况下来自模块名和本地标识符的散列）替换每个局部作用域标识符。

Extending 将源类名称添加到导出。

Extending 首先从其他模块扩展导入另一个模块，然后将类名添加到导出。

### 服务端和静态网站

[PostCSS-Modules](https://github.com/outpunk/postcss-modules) 允许使用 CSS Modules 进行静态构建，服务器端使用 Ruby，PHP 或任何其他语言或框架。
