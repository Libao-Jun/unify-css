# CSS 初始化样式表

> 保留有用默认样式，修复浏览器不一致性，使各浏览器表现更接近。

基于 Eric Meyer's [reset.css](https://meyerweb.com/eric/tools/css/reset/) 改进，适配现代 HTML5 元素。
提供 css/sass/less 三种格式，兼容 PostCSS/webpack/Vite 等主流工具链。

## 安装

```bash
# npm
npm install unify-css

# yarn
yarn add unify-css

# pnpm
pnpm add unify-css
```

## 使用方式

### HTML

```html
<link rel="stylesheet" href="/path/to/unify-css/reset.css" />
```

### CSS

```css
@import '/path/to/unify-css/reset.css';
```

### PostCSS and postcss-import

```css
@import 'unify-css';
```

### Webpack and css-loader

```js
import 'unify-css';
```

### Sass

```scss
@import '/path/to/unify-css/sass/reset';
```

### Less

```less
@import '/path/to/unify-css/less/reset';
```

## 浏览器对 `font: inherit;` 的支持

| 浏览器     | 对 `font: inherit;` 的支持 |
| ---------- | -------------------------- |
| IE6 / IE7  | ❌ 不支持或部分支持        |
| IE8        | ⚠️ 支持有限                |
| 现代浏览器 | ✅ 完全支持                |

## reset.css 解读

```css
.el {
	margin: 0;
	padding: 0;
	border: 0; /* 为什么不使用 border: none; 因为在重置 table 边框时，可能仍显示边框⚠️ */
	font: inherit; /* 统一继承所有字体属性 */
	vertical-align: baseline;
}
```

```css
/* 补充：表单元素特殊处理 */
button, input, select, textarea {
  background: transparent;   /* 移除非必要背景 */
  outline: none;             /* 移除默认轮廓，后续用 focus 自定义 */
  box-sizing: border-box;    /* 推荐加上，确保盒模型一致 */
}
```

## 与 reset-css 的差别

在原版 [Eric Meyer's reset.css](https://meyerweb.com/eric/tools/css/reset/) 基础上做了以下调整：

- **移除** HTML5 已弃用的元素：`applet`、`acronym`、`center`、`big`、`strike`、`tt`
- **新增** HTML5 语义元素支持：`main`、`datalist`、`colgroup`、`map`、`meter`、`optgroup`、`select`、`button`、`input`、`textarea`、`progress`
- **新增** 表单元素特殊处理：重置 `background`、`outline`，统一 `box-sizing`

## 参考

- [Eric Meyer's reset.css](https://meyerweb.com/eric/tools/css/reset/) — 经典 CSS Reset 原始版本
- [htmlreference.io](https://htmlreference.io/) — 包含所有 HTML 元素和属性
- [reset-css (npm)](https://www.npmjs.com/package/reset-css) — 另一个 Meyer reset 的 npm 封装
