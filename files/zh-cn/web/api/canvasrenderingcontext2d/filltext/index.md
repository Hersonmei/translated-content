---
title: CanvasRenderingContext2D.fillText()
slug: Web/API/CanvasRenderingContext2D/fillText
---

{{APIRef}}

**`CanvasRenderingContext2D.fillText()`** 是 Canvas 2D API 在 *(x, y)* 位置填充文本的方法。如果选项的第四个参数提供了最大宽度，文本会进行缩放以适应最大宽度。

参见 {{domxref("CanvasRenderingContext2D.strokeText()")}} 方法对文本进行描边。

## 语法

```js
void ctx.fillText(text, x, y, [maxWidth]);
```

### 参数

- `text`
  - : 使用当前的 {{domxref("CanvasRenderingContext2D.font","font")}}, {{domxref("CanvasRenderingContext2D.textAlign","textAlign")}}, {{domxref("CanvasRenderingContext2D.textBaseline","textBaseline")}} 和 {{domxref("CanvasRenderingContext2D.direction","direction")}} 值对文本进行渲染。
- `x`
  - : 文本起点的 x 轴坐标。
- `y`
  - : 文本起点的 y 轴坐标。
- `maxWidth` {{optional_inline}}
  - : 绘制的最大宽度。如果指定了值，并且经过计算字符串的值比最大宽度还要宽，字体为了适应会水平缩放（如果通过水平缩放当前字体，可以进行有效的或者合理可读的处理）或者使用小号的字体。

## 示例

### 使用 `fillText` 方法

这是一段使用 `fillText` 方法的简单的代码片段。

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");

ctx.font = "48px serif";
ctx.fillText("Hello world", 50, 100);
```

修改下面的代码并在线查看 canvas 的变化：

```html hidden
<canvas id="canvas" width="400" height="200" class="playable-canvas"></canvas>
<div class="playable-buttons">
  <input id="edit" type="button" value="Edit" />
  <input id="reset" type="button" value="Reset" />
</div>
<textarea id="code" class="playable-code">
ctx.font = "48px serif";
ctx.fillText("Hello world", 50, 100);</textarea>
```

```js hidden
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");
var textarea = document.getElementById("code");
var reset = document.getElementById("reset");
var edit = document.getElementById("edit");
var code = textarea.value;

function drawCanvas() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  eval(textarea.value);
}

reset.addEventListener("click", function() {
  textarea.value = code;
  drawCanvas();
});

edit.addEventListener("click", function() {
  textarea.focus();
})

textarea.addEventListener("input", drawCanvas);
window.addEventListener("load", drawCanvas);
```

{{ EmbedLiveSample('Playable_code', 700, 360) }}

## 规范描述

{{Specifications}}

## 浏览器兼容性

{{Compat("api.CanvasRenderingContext2D.fillText")}}

## 参见

- 接口定义， {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.strokeText()")}}
