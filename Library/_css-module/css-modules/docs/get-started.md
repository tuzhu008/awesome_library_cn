<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 设置 CSS Modules

CSS Modules 的工作原理是将各个 CSS 文件编译为 CSS 和数据。CSS 输出是正常的全局 CSS，可以直接注入到浏览器中，也可以连接在一起写入文件供生产使用。数据用于将您在文件中使用的人类可读名称映射到全局安全的输出 CSS。

目前有4种方法将 CSS Modules 集成到您的项目中。你应该看看这些项目的每一个更详细的设置说明。

### Webpack

[css-loader](https://github.com/webpack/css-loader) 内置了 CSS Modules。通过使用 `?modules` 标志来简单地激活它。我们在 [css-modules/webpack-demo](https://github.com/css-modules/webpack-demo) 中维护一个示例项目。

### Browserify

插件 [css-modulesify](https://github.com/css-modules/css-modulesify) 使您的 Browserify 构建能够 `require` CSS 文件，并将其编译成一个 CSS Module。对于一个使用该设置的示例项目，请检查 [css-modules/browserify-demo](https://github.com/css-modules/browserify-demo)。

### JSPM

这个实验性的 [jspm-loader-css-modules](https://github.com/geelen/jspm-loader-css-modules) 添加了 CSS Modules 支持 SystemJS 和 JSPM。在 [css-modules/jspm-demo](https://github.com/css-modules/jspm-demo) 中有一个简单的项目。

### NodeJS

[css-modules-require-hook](https://github.com/css-modules/css-modules-require-hook) 钩子的工作方式与 Browserify 插件类似，但将 NodeJS 的 `require` 的 CSS 文件解释为 CSS Modules。这在如何处理输出方面提供了完全的灵活性，对于服务器端渲染来说是理想的。

## 语言集成

### React

如果你使用 React，CSS Modules 是非常适合的。为了更好地集成 CSS Modules 和  React ，[react-css-modules](https://github.com/gajus/react-css-modules) 添加了 一个 `CSSModules` 高阶组件或 `@CSSModules` 注释

### Deku

如果你使用 Deku， Modules 是非常棒的。
[deku-css-modules] 允许简单地集成 CSS Modules & Deku。
