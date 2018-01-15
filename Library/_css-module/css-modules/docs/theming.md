<img src="https://raw.githubusercontent.com/css-modules/logos/master/css-modules-logo.png" width="150" height="150" />

# 主题

组件可以采用样式作为属性，而不是在组件中导入样式。这样可以使用不同的主题。用户甚至可以定义自定义主题。

``` css
/* component/theme-a.css */
.outer { background: green; }
.inner { color: blue; }
```

``` css
/* component/theme-b.css */
.outer { background: red; }
.inner { color: yellow; }
```

``` js
/* component/index.js */
export default class Component {
  constructor(theme) {
    this.theme = theme;
  }
  render() {
    var theme = this.theme;
    return '<div class="' + theme.outer + '">' +
      '<div class="' + theme.inner + '">' +
      '</div></div>';
  }
}
```

``` js
/* application */
import themeA from "component/theme-a.css";
import themeB from "component/theme-b.css";
import customTheme from "./custom-theme.css";

import Component from "component";

// use the Component
new Component(themeA);
new Component(themeB);
new Component(customTheme);
```
