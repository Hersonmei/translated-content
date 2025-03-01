---
title: 通常フロー
slug: Learn/CSS/CSS_layout/Normal_Flow
---
{{LearnSidebar}}

{{PreviousMenuNext("Learn/CSS/CSS_layout/Introduction", "Learn/CSS/CSS_layout/Flexbox", "Learn/CSS/CSS_layout")}}

この記事では、通常フロー、つまりレイアウトを変更していない場合のウェブページの要素のレイアウト方法について説明します。

| 前提知識: | HTML の基礎 ([HTML 入門](/ja/docs/Learn/HTML/Introduction_to_HTML)を学ぶ)、および CSS の機能の考え方 ([CSS 入門](/ja/docs/Learn/CSS/Introduction_to_CSS)を学ぶ)。 |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 学習目標: | 変更を加える前に、ブラウザーがデフォルトでウェブページをどのようにレイアウトするかを説明します。                                                                  |

レイアウトを紹介した前回のレッスンで詳しく説明したように、CSS を適用してふるまいを変更していない場合、ウェブページ上の要素は通常フローでレイアウトされます。そして、理解を深め始めるにつれ、その通常フローの中で要素の位置を調整したり、要素を完全に取り除くたりして、要素のふるまいを変更できます。通常フローで読み取り可能な、しっかりとよく構造化された文書から始めることは、どんなウェブページでも始めるための最良の方法です。それは、ユーザーが非常に制限されたブラウザーを使用している場合や、ページのコンテンツを読み上げるスクリーンリーダーなどのデバイスを使用している場合でも、コンテンツを読みやすくすることができます。さらに、通常フローは読み取り可能な文書を作成するように設計されているので、この方法で始めることで、レイアウトを変更するときに文書と戦うのではなく文書とともに作業します。

さまざまなレイアウト方法を深く掘り下げる前に、以前のモジュールで通常のドキュメントフローに関して検討したことのいくつかを再検討する価値があります。

## 要素はデフォルトでどのようにレイアウトされますか？

まず初めに、個々の要素ボックスは要素のコンテンツを取り、それからそれらの周りにパディング (padding、詰め物)、ボーダー (border、境界線) そしてマージン (margin、余白) を追加することによってレイアウトされます — これはまた以前に見たことがある[ボックスモデル](/ja/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)のことです。

デフォルトでは、[ブロックレベル要素](/ja/docs/Web/HTML/Block-level_elements)のコンテンツは、その親要素の幅の 100% で、そのコンテンツと同じ高さです [インライン要素](/ja/docs/Web/HTML/Inline_elements)は、コンテンツと同じ高さで、コンテンツと同じ幅です。インライン要素に幅や高さを設定することはできません — それらはブロックレベル要素のコンテンツの中にあるだけです。この方法でインライン要素のサイズを制御したい場合は、`display: block;` を使用してブロックレベル要素のようにふるまうように設定する必要があります (あるいは、`display: inline-block;` で、両方の特性を混在させます)。

それは個々の要素を説明していますが、要素がどのように相互作用するかについてはどうでしょうか？ 通常のレイアウトフロー (レイアウト入門の記事に記載) は、ブラウザーのビューポート内に要素を配置するシステムです デフォルトでは、ブロックレベル要素は、親の[書字方向モード](/ja/docs/Web/CSS/writing-mode) (writing mode、_初期_ は horizontal-tb) に基づいて*ブロックのフロー方向* にレイアウトされます — 各要素は、最後の要素の下の新しい行に表示され、それらに設定されたマージンで区切られます したがって英語やその他の横書きで、上から下へ改行する書字方向モードでは、ブロックレベル要素は垂直にレイアウトされます。

インライン要素は異なるふるまいをします — 新しい行に現れません。代わりに、親ブロックレベル要素の幅の内側にマージンがある限り、それらは互いに同じ行に配置され、隣接する (または折り返された) テキストコンテンツに配置されます。スペースがなければ、あふれているテキストや要素は新しい行に移動します。

隣接する 2 つの要素の両方にマージンが設定されていて、2 つのマージンが接触している場合、2 つのうち大きい方が残り、小さい方が消えます — これは[マージンの相殺](/ja/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing) (margin collapsing) と呼ばれます。

これらすべてを説明する簡単な例を見てみましょう。

```html
<h1>基本的なドキュメントフロー</h1>

<p>これは基本的なブロックレベル要素です。隣接するブロックレベル要素は下の新しい行に配置されています。</p>

<p>デフォルトでは、親要素の幅の 100% にまたがり、子コンテンツと同じ高さになります。幅と高さの合計は、コンテンツ + パディング + ボーダーの幅/高さです。</p>

<p>マージンによって分けられています。マージンの相殺のため、両方ではなく、1 つのマージンの幅で区切られます。</p>

<p><span>これ</span>および<span>これのような</span>インライン要素は、同じ行に配置され、同じ行にスペースがある場合は隣接するテキストノードに配置されます。オーバーフローするインライン要素は<span>可能であれば新しいラインに折り返され (これのようにテキストを含む)</span>、そうでなければ次の画像のように単に新しい行に進むでしょう。<img src="long.jpg" alt="snippet of cloth"></p>
```

```css
body {
  width: 500px;
  margin: 0 auto;
}

p {
  background: rgba(255,84,104,0.3);
  border: 2px solid rgb(255,84,104);
  padding: 10px;
  margin: 10px;
}

span {
  background: white;
  border: 1px solid black;
}
```

{{ EmbedLiveSample('Normal_Flow', '100%', 500) }}

## まとめ

通常フロー、およびブラウザーがデフォルトでどのようにレイアウトするかを理解したので、次にこのデフォルトの `display` を変更してデザインに必要なレイアウトを作成する方法を理解することに進みます。

{{PreviousMenuNext("Learn/CSS/CSS_layout/Introduction", "Learn/CSS/CSS_layout/Flexbox", "Learn/CSS/CSS_layout")}}

## このモジュール内の文書

- [CSS レイアウト入門](/ja/docs/Learn/CSS/CSS_layout/Introduction)
- [通常フロー](/ja/docs/Learn/CSS/CSS_layout/Normal_Flow)
- [フレックスボックス](/ja/docs/Learn/CSS/CSS_layout/Flexbox)
- [グリッド](/ja/docs/Learn/CSS/CSS_layout/Grids)
- [フロート](/ja/docs/Learn/CSS/CSS_layout/Floats)
- [位置指定](/ja/docs/Learn/CSS/CSS_layout/Positioning)
- [段組みレイアウト](/ja/docs/Learn/CSS/CSS_layout/Multiple-column_Layout)
- [レスポンシブデザイン](/ja/docs/Learn/CSS/CSS_layout/Responsive_Design)
- [メディアクエリーの初心者向けガイド](/ja/docs/Learn/CSS/CSS_layout/Media_queries)
- [過去のレイアウト方法](/ja/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods)
- [古いブラウザーのサポート](/ja/docs/Learn/CSS/CSS_layout/Supporting_Older_Browsers)
- [基礎的なレイアウトの理解](/ja/docs/Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension)
