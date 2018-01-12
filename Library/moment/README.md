[![Join the chat at https://gitter.im/moment/moment](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/moment/moment?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![NPM version][npm-version-image]][npm-url] [![NPM downloads][npm-downloads-image]][npm-url] [![MIT License][license-image]][license-url] [![Build Status][travis-image]][travis-url]
[![Coverage Status](https://coveralls.io/repos/moment/moment/badge.svg?branch=develop)](https://coveralls.io/r/moment/moment?branch=develop)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fmoment%2Fmoment.svg?type=shield)](https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fmoment%2Fmoment?ref=badge_shield)

一个轻量级的 JavaScript date 库，用于解析、验证、操作和格式化日期。

**[英文文档](http://momentjs.com/docs/)**

**[中文文档](http://momentjs.cn/docs/)**

**[中文翻译](http://moment.bestajax.com/docs/)**

## Port to ECMAScript 6 (version 2.10.0)

Moment 2.10.0 并没有带来任何新功能，但是现在代码已经被写入了 ECMAScript 6模块，并被放在 `src/` 里面。 之前的 `moment.js`、`locale/*.js` 和 `test/moment/*.js`、 `test/locale/*.js` 包含了项目的源代码。 现在源代码在 `src/` 中，临时构建（ECMAScript 5）文件放在 `build/umd/`（用于在开发过程中运行测试），并且 `moment.js` 和 `locale/*.js` 文件仅在发布时更新。

如果你想使用特定版本的代码，确保运行 `grunt transpile update-index`，所以 `moment.js` 和  `locales/*.js` 与 `src/*` 同步。 我们可能会把它放在未来的提交钩子中。

## 升级到 2.0.0

版本 2.0.0 有一些小的向后不兼容的变化。[见这里的完整说明](https://gist.github.com/timrwood/e72f2eef320ed9e37c51#backwards-incompatible-changes)

  * 更改语言序号方法以返回数字+序号，而不是只是序号。

  * 更改了两位数的解析截止年份，以匹配strptime。

  * 删除了 `moment#sod` 和 `moment#eod`，以支持 `moment#startOf` 和 `moment#endOf`.

  * `moment.humanizeDuration()` 以支持 `moment.duration().humanize()`

  * 从顶级命名空间中删除了 lang 数据对象。

  * 重复的 `Date` 被传递给 `moment()` 而不是引用它。

## [更新日志](https://github.com/moment/moment/blob/develop/CHANGELOG.md)

## [贡献](https://github.com/moment/moment/blob/develop/CONTRIBUTING.md)

我们正在寻找共同维护者! 如果你想成为一名时间管理者，请写信给我 [ichernev](https://github.com/ichernev)。

## License

Moment.js is freely distributable under the terms of the [MIT license](https://github.com/moment/moment/blob/develop/LICENSE).

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fmoment%2Fmoment.svg?type=large)](https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fmoment%2Fmoment?ref=badge_large)

[license-image]: http://img.shields.io/badge/license-MIT-blue.svg?style=flat
[license-url]: LICENSE

[npm-url]: https://npmjs.org/package/moment
[npm-version-image]: http://img.shields.io/npm/v/moment.svg?style=flat
[npm-downloads-image]: http://img.shields.io/npm/dm/moment.svg?style=flat

[travis-url]: http://travis-ci.org/moment/moment
[travis-image]: http://img.shields.io/travis/moment/moment/develop.svg?style=flat
