---
title: ':only-of-type'
slug: Web/CSS/:only-of-type
---

{{ CSSRef() }}

## 概述

CSS [伪类](/zh-CN/docs/Web/CSS/Pseudo-classes) `:only-of-type` 代表了任意一个元素，这个元素没有其他相同类型的兄弟元素。

> **备注：** 根据原来的定义，被选择的元素必须具有父元素。直到 Selectors Level 4 开始，这个要求就不是必须的了。

## 语法

```
element:only-of-type { style properties }
```

## Example

#### HTML

```html
<main>
  <div>I am `div` #1.</div>
  <p>I am the only `p` among my siblings.</p>
  <div>I am `div` #2.</div>
  <div>I am `div` #3.
    <i>I am the only `i` child.</i>
    <em>I am `em` #1.</em>
    <em>I am `em` #2.</em>
  </div>
</main>
```

#### CSS

```css
main :only-of-type {
  color: red;
}
```

#### 结果

{{EmbedLiveSample('Example','100%',180)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("css.selectors.only-of-type")}}

## 参见

- {{Cssxref(":only-child")}}
- {{Cssxref(":first-of-type")}}
- {{Cssxref(":last-of-type")}}
- {{Cssxref(":nth-of-type")}}
