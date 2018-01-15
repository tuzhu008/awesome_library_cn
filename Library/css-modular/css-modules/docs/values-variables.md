<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 导出值变量

可以在 css 模块中导出值，类似于在 less 或 sass 中使用变量。

只需确保使用了 postcss 和 [postcss-modules-values](https://github.com/css-modules/postcss-modules-values) 插件。

现在设置值/变量

**colors.css**

```css
@value blue: #0c77f8;
@value red: #ff0000;
@value green: #aaf200;
```

然后将它们导入到您的组件 css 模块中

**demo.css**

```css
/* import your colors... */
@value colors: "./colors.css";
@value blue, red, green from colors;

.button {
  color: blue;
  display: inline-block;
}
```

## Example webpack.config for postcss-modules-values

```js
var path = require('path');
var webpack = require('webpack');
var ExtractTextPlugin = require('extract-text-webpack-plugin');
var values = require('postcss-modules-values');

module.exports = {
  entry: ['./src/index'],
  output: {
    filename: 'bundle.js',
    path: path.join(__dirname, 'public'),
    publicPath: '/public/'
  },
  module: {
    loaders: [
      { test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
      { test: /\.css$/, loader: ExtractTextPlugin.extract('style-loader', 'css-loader?modules&importLoaders=1&localIdentName=[name]__[local]___[hash:base64:5]!postcss-loader') }
    ]
  },
  postcss: [
    values
  ],
  plugins: [
    new ExtractTextPlugin('style.css', { allChunks: true })
  ]

};
```
