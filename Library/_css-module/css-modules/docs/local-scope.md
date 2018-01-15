<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# CSS Modules — 局部作用域

CSS Modules 的第一个也是最基本的特性是类选择器，默认情况下，是**局部的**。 所以，如果你写：

```css
.backdrop {}
.prompt {}
.pullquote {}
```

`backdrop`，`field` 和 `pullquote` 类是*这个文件的局部*。这意味着他们不会污染全局命名空间，所以你可以自由地使用任何你喜欢的名字。 您可以通过导入或在您的 JS 文件中 require 它们来编译它们。这些例子将使用 React 语法，但是当然它不以任何特定的方式与 React 绑定。

```js
import styles from "./style.css"

const Component = props => {
  return (
    <div className={styles.backdrop}>
      <div className={styles.prompt}>
      </div>
      <div className={styles.pullquote}>
      </div>
   </div>
  )
}
```
