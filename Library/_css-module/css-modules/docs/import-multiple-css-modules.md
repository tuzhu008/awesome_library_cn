<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 将多个 css 模块导入到一个组件中

您可以使用 `Object.assign` 将多个 css 模块导入到一个组件或函数中。

例如，如果您将一个按钮 css 模块导入到 Demo 组件，那么将其添加到组件默认样式中。

```js
let styles = {}
import demo from './Demo.css'
import fancyButton from 'css-fancy-button'
Object.assign(styles, fancyButton, demo)
```

您甚至可以从 npm 中导入 css 模块。例如 [pure-css](https://github.com/StevenIseki/pure-css)

```sh
npm install pure-css --save-dev
```

然后在你的组件终....开始使用 pure-css 的样式

```js
import { buttons, grids } from 'pure-css'
```

一个完整的 demo 组件示例，其中导入了两个 css 模块。

```jsx
import React from 'react'
let styles = {}
import demo from './Demo.css'
import fancyButton from 'css-fancy-button'
Object.assign(styles, fancyButton, demo)

function Demo( props) {

    const { route } = props;

    return (
    	<div className={styles.demo}>
    		<button className={styles.fancyButton}>press me</button>
       	</div>
    );
}

export default Demo
```
