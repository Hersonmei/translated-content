---
title: CSS（层叠样式表）
slug: Web/CSS
---

{{CSSRef}}

**层叠样式表** (Cascading Style Sheets，缩写为 **CSS**），是一种 [样式表](/zh-CN/docs/DOM/stylesheet) 语言，用来描述 [HTML](/zh-CN/docs/HTML) 或 [XML](/zh-CN/docs/XML_介绍)（包括如 [SVG](/zh-CN/docs/SVG)、[MathML](/zh-CN/docs/Web/MathML)、[XHTML](/zh-CN/docs/XHTML) 之类的 XML 分支语言）文档的呈现。CSS 描述了在屏幕、纸质、音频等其它媒体上的元素应该如何被渲染的问题。

CSS 是**开放网络**的核心语言之一，由 [W3C 规范](http://w3.org/Style/CSS/#specs) 实现跨浏览器的标准化。CSS 节省了大量的工作。 样式可以通过定义保存在外部.css 文件中，同时控制多个网页的布局，这意味着开发者不必经历在所有网页上编辑布局的麻烦。CSS 被分为不同等级：CSS1 现已废弃， CSS2.1 是推荐标准， [CSS3](/zh-CN/docs/CSS/CSS3) 分成多个小模块且正在标准化中。

- **CSS** 介绍

  如果你是 Web 开发的新手，请务必阅读我们的 [CSS 基础](/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics)文章以学习 CSS 的含义和用法。

- **CSS** 教程

  我们的 [CSS 学习区](/zh-CN/docs/Learn/CSS)包含了丰富的教程，它们覆盖了全部基础知识，能使你在 CSS 之路上从初出茅庐到游刃有余。

- **CSS** 参考

  针对资深 Web 开发者的[详细参考手册](/zh-CN/docs/Web/CSS/Reference)，描述了 CSS 的各个属性与概念。

## 教程

我们的 [CSS 学习区](/zh-CN/docs/Learn/CSS) 以多模块、零基础为特色进行 CSS 的教学 —— 这也就意味着你不需要任何知识基础。

- [学习 CSS 第一步](/zh-CN/docs/Learn/CSS/First_steps)
  - : CSS（层叠样式表）用于设置网页的样式及布局——比如，可以更改内容的字体、颜色、大小以及间距，或是将其分列，或是添加动画及赋予内容其它装饰性的特征。本模块将通过阐述基本原理，展示语法示例，以及如何与 HTML 相联系三方面，为你日后精通 CSS 提供一个友好的开端。
- [CSS 构建](/zh-CN/docs/Learn/CSS/Building_blocks)

  - : 本模块是[学习 CSS 第一步](/zh-CN/docs/Learn/CSS/First_steps)的延续，相信你已经熟悉了这门语言及它的语法，并拥有一些使用它的基本经验，是时候更进一步了。本模块着眼于层叠和继承、所有可用的选择器类型、单位、大小、背景、边框、调试等等。

    其目的在于先为你提供编写功能强大的 CSS 工具包，了解所有基础理论。之后再进行进一步的学习，诸如[样式化文本](/zh-CN/docs/Learn/CSS/为文本添加样式)和[CSS 布局](/zh-CN/docs/Learn/CSS/CSS_layout)

- [样式化文本](/zh-CN/docs/Learn/CSS/Styling_text)
  - : 在学习了 CSS 语言基础知识的基础上，你需要关注的下一个重点是样式化文本——这是使用 CSS 时最常用的场景之一。在这一模块将学习文本样式设置的基础知识，包括设置字体、粗体、斜体、行、字符间距、阴影以及其他文本属性。我们通过在页面上应用自定义的字体以及样式化的列表、链接来完善本模块。
- [CSS 布局](/zh-CN/docs/Learn/CSS/CSS_layout)
  - : 到这里，我们已经了解了 CSS 基础：如何样式化文本，以及如何样式化和操作内置个人内容的盒模型。现在是时候研究“如何相对于可视区域将你的盒子彼此间放置于正确位置”了。我们到此已经覆盖了所有预备知识，因此现在能够深入学习 CSS 布局，研究不同的显示设置，包括浮动和定位在内的传统布局方法，以及像如弹性盒（flexbox）之类新近流行的布局工具。
- [解决常见的 CSS 相关问题](/zh-CN/docs/Learn/CSS/Howto)
  - : 本模块提供了一些内容链接，这些内容很好的回答了在创建网页时使用 CSS 所遇到的常见问题。

## 参考

- [CSS 参考](/zh-CN/docs/Web/CSS/Reference): 针对资深 Web 开发者的详细参考手册，其中描述了 CSS 的各个属性和概念。
- CSS 关键概念:

  - [语言语法和形式](/zh-CN/docs/CSS/Syntax)（The [syntax and forms of the language](/zh-CN/docs/CSS/Syntax)）
  - [特殊性（另译优先级）](/zh-CN/docs/CSS/Specificity)、[继承](/zh-CN/docs/CSS/inheritance)和[级联](/zh-CN/docs/Web/CSS/Cascade)（[Specificity](/zh-CN/docs/CSS/Specificity), [inheritance](/zh-CN/docs/CSS/inheritance) and [the Cascade](/zh-CN/docs/Web/CSS/Cascade)）
  - [盒子模型](/zh-CN/docs/CSS/box_model)和[外边距合并](/zh-CN/docs/CSS/margin_collapsing)（[Box model](/zh-CN/docs/CSS/box_model) and [margin collapse](/zh-CN/docs/CSS/margin_collapsing)）
  - [包含块](/zh-CN/docs/Web/CSS/All_About_The_Containing_Block)（The [containing block](/zh-CN/docs/Web/CSS/Containing_block)）
  - [堆叠](/zh-CN/docs/CSS/Understanding_z-index/The_stacking_context)和[块格式化](/zh-CN/docs/CSS/block_formatting_context)上下文（[Stacking](/zh-CN/docs/CSS/Understanding_z-index/The_stacking_context) and [block-formatting](/zh-CN/docs/CSS/block_formatting_context) contexts）
  - [初始值](/zh-CN/docs/CSS/initial_value)、[计算值](/zh-CN/docs/Web/CSS/computed_value)、[应用值](/zh-CN/docs/CSS/used_value)和[实际值](/zh-CN/docs/CSS/actual_value)（[Initial](/zh-CN/docs/CSS/initial_value), [computed](/zh-CN/docs/CSS/computed_value), [used](/zh-CN/docs/CSS/used_value), and [actual](/zh-CN/docs/CSS/actual_value) values）
  - [CSS 简写属性](/zh-CN/docs/Web/CSS/Shorthand_properties)（[CSS shorthand properties](/zh-CN/docs/CSS/Shorthand_properties)）
  - [CSS 弹性盒子布局](/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout) ([CSS Flexible Box Layout](/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout))
  - [CSS 网格布局](/zh-CN/docs/Web/CSS/CSS_Grid_Layout) ([Grid Layout](/zh-CN/docs/Web/CSS/CSS_Grid_Layout))
  - [媒体查询](/zh-CN/docs/Web/CSS/媒体查询)
  - [动画](/zh-CN/docs/Web/CSS/animation)

## 参考书

《[CSS layout cookbook](/zh-CN/docs/Web/CSS/Layout_cookbook)》一书的目的是将一些也许你将要在自己的网站中实现的、常用的布局模式的方法汇集在一起，并且还提供了代码使你可以在项目中作为基础来使用。这些方法突出表现了同一布局规范的不同使用方式，作为开发者你可以自由选择自己想要的方式来实现。

## CSS 开发工具

- [W3C CSS Validation Service（万维网联盟 CSS 验证服务）](http://jigsaw.w3.org/css-validator/) 用以检查 CSS 是否有效。这是非常有价值的调试工具。
- [Firefox 开发工具](/zh-CN/docs/Tools) 允许通过 [页面查看器](/zh-CN/docs/Tools/Page_Inspector) 和 [样式编辑器](/zh-CN/docs/Tools/Style_Editor) 工具查看和实时编辑页面的 CSS。
- Firefox 的 [Web Developer 扩展](https://addons.mozilla.org/zh-CN/firefox/addon/60)，也允许实时查看和编辑网站的 CSS。
- [各种各样的其他工具](/zh-CN/docs/Web/CSS/Tools)。

## 自身的错误

- Firefox: {{bug(1323667)}}

## 相关链接

- [CSS 演示说明](/zh-CN/docs/Web/%E6%BC%94%E7%A4%BA%E8%AF%B4%E6%98%8E#CSS)：最新活跃的 CSS 技术——创造力的推动。
- 常与 CSS 一起应用的 Web 语言：[HTML](/zh-CN/docs/HTML)、[SVG](/zh-CN/docs/SVG)、[MathML](/zh-CN/docs/Web/MathML)、{{Glossary("XHTML", "", 1)}} 以及 [XML](/zh-CN/docs/XML_介绍)。
- Mozilla CSS 扩展用途技术：[XUL](/zh-CN/docs/Mozilla/Tech/XUL)、[Firefox](/zh-CN/Firefox)、以及 [Thunderbird 扩展](/zh-CN/docs/Mozilla/Thunderbird)与[主题](/zh-CN/docs/Mozilla/Add-ons/Themes)。
- [Mozilla 邮件列表](https://lists.mozilla.org/listinfo/dev-tech-layout)
- [StackOverflow 上 css 相关的问题](http://stackoverflow.com/questions/tagged/css)
