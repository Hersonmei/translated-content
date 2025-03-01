---
title: 'HTML: アクセシビリティの基礎'
slug: Learn/Accessibility/HTML
---
{{LearnSidebar}}{{PreviousMenuNext("Learn/Accessibility/What_is_Accessibility","Learn/Accessibility/CSS_and_JavaScript", "Learn/Accessibility")}}

正確な HTML 要素が、常に正しい目的で使用されているかを確認するだけで、たくさんのウェブコンテンツがアクセシブルになります。 ここでは、最大限のアクセシビリティを確保するために、HTML をどのように使用できるかについて詳しく説明します。

| 前提知識: | 基本的なコンピュータの知識、HTML に関する基本的な理解 ([HTML 概論](/ja/docs/Learn/HTML/Introduction_to_HTML) を参照)、[アクセシビリティとは何か](/ja/docs/Learn/Accessibility/What_is_accessibility) に関する理解。 |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 学習目標: | HTML のうち、どの機能にアクセシビリティ上の利点があるのか、また、自身のウェブドキュメントでそうした機能を適切に使うにはどうしたらよいのか、ということに精通すること。                                               |

## HTML とアクセシビリティ

HTML について学習を進めるのにつれて——資料をたくさん読んだり、たくさんの例を見たりするのにつれて——共通の主題を繰り返し見続けることになるでしょう。つまり、意味的な (セマンティックな) HTML を使うことの重要性という主題です (これは、POSH すなわち Plain Old Semantic HTML (簡潔な昔ながらの意味的 HTML) と呼ばれることがあります)。これが意味することは、できる限り、ふさわしい HTML 要素をふさわしい目的に使う、ということです。

これが何故それほど重要なのか、不思議に思うかもしれません。何しろ、CSS と JavaScript の組み合わせを使って、ほぼすべての HTML 要素を、どのような仕方であれ望みどおりに振る舞わせることができるわけですから。たとえば、サイト上で動画を再生するためのコントロール・ボタンを、次のようにマークアップすることもできます。

```html
<div>動画を再生する</div>
```

けれども、後にさらに詳しく見るとおり、この役割にふさわしい要素を使うことには、とても意味があります。

```html
<button>動画を再生する</button>
```

HTML の `<button>` は、ある種の適切なスタイルが (おそらくそのスタイルを上書きしたいと思うでしょうが) デフォルトで適用されているだけでなく、組み込みのキーボード・アクセシビリティも備えています。つまり、`<button>` 同士の間をタブで移動できますし、リターン / エンターを使って `<button>` をアクティブにできます。

もしプロジェクトの最初から首尾一貫して意味的な HTML を書くならば、意味的な HTML を書く方が非意味的な (駄目な) マークアップを書くよりも長くなったりはしません。それに、意味的な HTML には、アクセシビリティ以外の他の利点もあります。

1. **より開発しやすい**——上述のとおり、ある種の機能がただで手に入りますし、それに、より理解しやすいという点はまず間違いないところです。
2. **モバイル機器に関して、より優れている**——意味的な HTML は非意味的なスパゲッティ・コードよりも、ファイルサイズの点でほぼ間違いなく軽量ですし、レスポンシブにするのも簡単です。
3. **SEO に関しても良好である**——検索エンジンは、非意味的な `<div>` などに含まれるキーワードよりも、見出しやリンクなどの中のキーワードの方に重みを持たせているので、ドキュメントが顧客に見つけてもらいやすくなるでしょう。

それでは、ここからアクセシブルな HTML をより詳しく見てゆきましょう。

> **Note:** 自分のローカルコンピューターにスクリーンリーダーを用意することは良い考えです。そうすれば、以下に示す例について、ある程度のテストができます。より詳しくは、[Screenreaders guide](/ja/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#Screenreaders) を参照してください。

## 良いセマンティクス

良いセマンティクスの重要性について、そして、ふさわしい役割にふさわしい HTML 要素を使うべきである理由については、すでに述べました。このことは無視してはなりません。なぜなら、適切に扱わないとアクセシビリティがひどく損なわれてしまう主な箇所のうちの一つだからです。

ウェブ上のどこかで、実は、人々は HTML のマークアップに関してとても変なことをしています。HTML の悪用のうちには、まだ完全に忘れ去られたわけではない過去の遺物的な慣行によるものもあり、ただ単純な無知によるものもあります。いずれにせよ、そうした駄目なコードは、どこで見たものであれ、可能な場合にはいつでも置き換えるべきです。

ときには、駄目なマークアップを取り去れる状況にいるとは限りません。自分で完全に制御しきれるわけではない、ある種のサーバーサイド・フレームワークによって、生成されたページなのかもしれません。あるいは、自分のページ上に、自分が管理していない (広告バナーのような) 第三者のコンテンツを含むかもしれません。

しかし、目標は「全か無か」というものではありません。自分ができる改善のことごとくが、アクセシビリティの理念に役立つことでしょう。

### テキストコンテンツ

スクリーンリーダーのユーザーが得られる最良のアクセシビリティ支援の一つは、見出しや段落やリストなどの適切なコンテンツ構造です。きちんと意味を備えた例は、以下のようなものになるでしょう。

```html example-good
<h1>見出し</h1>

<p>これは文書のうちの最初のセクションです。</p>

<p>ここにも、もう一つ段落を足すつもり。</p>

<ol>
  <li>ここには</li>
  <li>読んでもらいたいことの</li>
  <li>リストがあります。</li>
</ol>

<h2>下位見出し</h2>

<p>これは文書のうちの最初のサブセクションです。みんながこのコンテンツを見つけられるといいな!</p>

<h2>2 番目の下位見出し</h2>

<p>これはコンテンツのうちで 2 番目のサブセクションです。この前のものより面白いと思いますよ。</p>
```

スクリーンリーダーを使って試せるように、より長いテキストのバージョンを用意してあります ([good-semantics.html](http://mdn.github.io/learning-area/accessibility/html/good-semantics.html) を参照)。これの全体をナビゲートして (経巡って) みれば、これはとても見通しが得やすいものだということがわかるでしょう。

1. コンテンツの中を進んでゆくのにつれて、スクリーンリーダーは各ヘッダを読み上げて、どれが見出しでどれが段落なのかといったことを知らせてくれます。
2. どのような速度が快適であるにせよ、その速度で進んでいけるように、スクリーンリーダーは各要素の後で停止します。
3. 多くのスクリーンリーダーでは、次の見出し / 前の見出しへとジャンプできます。
4. 多くのスクリーンリーダーでは、すべての見出しの一覧を取り出せます。それらの見出しを、特定のコンテンツを見つけるための手軽な目次のようにも使えます。

ときには、たとえば以下のように、体裁用の HTML や改行を使って見出しや段落などを書く人もいます。

```html example-bad
<font size="7">見出し</font>
<br><br>
これは文書のうちの最初のセクションです。
<br><br>
ここにも、もう一つ段落を足すつもり。
<br><br>
1. ここには
<br><br>
2. 読んでもらいたいことの
<br><br>
3. リストがあります。
<br><br>
<font size="5">下位見出し</font>
<br><br>
これは文書のうちの最初のサブセクションです。みんながこのコンテンツを見つけられるといいな!
<br><br>
<font size="5">2 番目の下位見出し</font>
<br><br>
これはコンテンツのうちで 2 番目のサブセクションです。この前のものより面白いと思いますよ。
```

より長いバージョンをスクリーンリーダーで試してみれば ([bad-semantics.html](http://mdn.github.io/learning-area/accessibility/html/bad-semantics.html) を参照)、とても良い体験が得られる、とはいかないことでしょう。スクリーンリーダーは、標識として使えるものを何も得られないので、有用な目次は取得できません。また、ページ全体を単一の巨大な塊として見ることになるので、ページ全体が一度にひとかたまりで読み上げられるだけなのです。

アクセシビリティ以外の他の問題もあります。たとえば、CSS を使ってコンテンツにスタイルをつけることや、あるいは、JavaScript でコンテンツを操作することが、より難しくなるのです。なぜなら、セレクターとして使える要素がないからです。

#### 明確な言葉を使う

使っている言い回しもアクセシビリティに影響を与えることがあります。一般に、過度に複雑ではない、明確な言葉を使うべきです。また、不必要な専門用語 (ジャーゴン) や俗語を使わないようにしましょう。これは、認知的な障害またはその他の障害を抱える人たちの助けとなるだけではありません。母語以外で書かれたテキストの読者や、年少者の助けにもなりますし、実際のところあらゆる人の助けになります! それに加えて、スクリーンリーダーによって明確に読み上げられない言い回しや文字を使うことを避けるように努めるべきです。たとえば、以下のようなことです。

- やめられるものなら、ダッシュを使わないようにしましょう。「5–7」と書く代わりに「5 から 7」と書きましょう。
- 略語を展開しましょう。「Jan」と書く代わりに「January」と書きましょう。
- 少なくとも一、二回は、頭文字語を展開しましょう。最初の出現箇所で「HTML」と書く代わりに、「Hypertext Markup Language すなわち HTML」と書きましょう。

### ページレイアウト

古き悪しき時代には、HTML テーブルを使って (つまり、ヘッダー、フッター、サイドバー、主要コンテンツの列、などなどを含む、別々のテーブル・セルを使って)、ページレイアウトを作成していたものです。これは良い考えではありません。なぜなら、スクリーンリーダーが、こんがらがった読み上げを発する可能性が高いからです。特に、レイアウトが複雑で多くの入れ子になったテーブルがある場合には、そうなりがちです。

[table-layout.html](http://mdn.github.io/learning-area/accessibility/html/table-layout.html) の例を試してみてください。これは、以下のような感じになっています。

```html
<table width="1200">
      <!-- 主要な見出しの行 -->
      <tr id="heading">
        <td colspan="6">

          <h1 align="center">Header</h1>

        </td>
      </tr>
      <!-- ナビゲーション・メニューの行 -->
      <tr id="nav" bgcolor="#ffffff">
        <td width="200">
          <a href="#" align="center">Home</a>
        </td>
        <td width="200">
          <a href="#" align="center">Our team</a>
        </td>
        <td width="200">
          <a href="#" align="center">Projects</a>
        </td>
        <td width="200">
          <a href="#" align="center">Contact</a>
        </td>
        <td width="300">
          <form width="300">
            <input type="search" name="q" placeholder="Search query" width="300">
          </form>
        </td>
        <td width="100">
          <button width="100">Go!</button>
        </td>
      </tr>
      <!-- 間隔をあけるための詰め物の行 -->
      <tr id="spacer" height="10">
        <td>

        </td>
      </tr>
      <!-- 主要なコンテンツと余談の行 -->
      <tr id="main">
        <td id="content" colspan="4" bgcolor="#ffffff">

          <!-- 主要なコンテンツがここに来る -->
        </td>
        <td id="aside" colspan="2" bgcolor="#ff80ff" valign="top">
          <h2>Related</h2>

          <!-- 余談的コンテンツがここに来る -->

        </td>
      </tr>
      <!-- 間隔をあけるための詰め物の行 -->
      <tr id="spacer" height="10">
        <td>

        </td>
      </tr>
      <!-- フッターの行 -->
      <tr id="footer" bgcolor="#ffffff">
        <td colspan="6">
          <p>©Copyright 2050 by nobody. All rights reversed.</p>
        </td>
      </tr>
    </table>
```

スクリーンリーダーを使ってこれを読んで回ろうとすると、おそらくスクリーンリーダーは、見るべきテーブルがありますよ、と教えてくれるでしょう (もっとも、一部のスクリーンリーダーは、テーブル・レイアウトとデータ・テーブルとの違いを推測できるでしょうが)。すると、(使っているスクリーンリーダーによりますが) オブジェクトとしてのテーブルのところまで行って、そのテーブルの項目をそれぞれ別々に見て、それからやっと、テーブルから抜けて元の場所に戻り、コンテンツを読んで回ることを続ける、というふうにせざるを得ない可能性が高いでしょう。

テーブル・レイアウトは過去の遺物です。テーブル・レイアウトは、CSS のサポートがブラウザーに広く行き渡っていなかった当時には意味を持っていましたが、スクリーンリーダーのユーザーに対して混乱を巻き起こします。しかも、他の多くの理由でも有害です (テーブルの乱用ですし、ほぼ間違いなくマークアップをより多く要しますし、デザインの柔軟さを損ねます)。テーブル・レイアウトをしてはなりません!

直前にした体験を、[よりモダンなウェブサイトの構成例](http://mdn.github.io/learning-area/html/introduction-to-html/document_and_website_structure/) (以下のような感じです) と比較することで、上記のような (テーブル・レイアウトは駄目だという) 主張の正しさを確認できます。

```html
<header>
  <h1>Header</h1>
</header>

<nav>
  <!-- 主なナビゲーションはここです。 -->
</nav>

<!-- ここにページの主要コンテンツが来ます。 -->
<main>

  <!-- 主要コンテンツは記事を含みます。 -->
  <article>
    <h2>Article heading</h2>

    <!-- 記事の中身はここです。 -->
  </article>

  <aside>
    <h2>Related</h2>

    <!-- 余談の中身はここです。 -->
  </aside>

</main>

<!-- そしてここには、ウェブサイトの全ページを通じて使う主要なフッターが来ます。 -->

<footer>
  <!-- フッターの中身はここです。 -->
</footer>
```

よりモダンな構造の例をスクリーンリーダーで試してみれば、もはやレイアウト・マークアップが妨げになることもなく、コンテンツの読み上げを混乱させることもない、とわかるでしょう。また、これは、コード・サイズの点で、より無駄がなく、より小さくなっています。これが意味することは、コードの保守が容易になるということ、そして、ユーザがダウンロードするのに帯域幅が小さくて済むということです (特に、接続が遅い人たちにとってはこれが効きます)。

レイアウトを作る際に考慮すべきもう一つの事柄は、上記の例に見られるように HTML5 の意味的要素を用いることです ([コンテンツセクショニング](/ja/docs/Web/HTML/Element#Content_sectioning) を参照)。 入れ子になった {{htmlelement("div")}} 要素だけを使ってレイアウトを作ることもできますが、適切なセクショニング (区分け) 要素を使って、主要なナビゲーション ({{htmlelement("nav")}}) やフッター ({{htmlelement("footer")}}) や繰り返し現れるコンテンツ単位 ({{htmlelement("article")}}) などを囲う方が良いのです。これらの区分け要素は、いまナビゲートしている最中のコンテンツについての追加的な手がかりをユーザーに与えられるように、スクリーンリーダー (および他のツール) に追加的な意味 (セマンティクス) を提供してくれます (スクリーンリーダー・サポートとはどのようなものなのかについての考え方に関しては、[Screen Reader Support for new HTML5 Section Elements](http://www.weba11y.com/blog/2016/04/22/screen-reader-support-for-new-html5-section-elements/) を参照)。

> **Note:** コンテンツは、ちゃんと意味的なものにしておき、レイアウトも魅惑的にしておくだけでなく、ソース順において論理的に意味をなすようにもしておくべきです。あとで CSS を使えば必ず望みどおりの場所にコンテンツを配置できますが、ソース順は、その順で読み始めるのが適切なようにしておくべきです。そうすれば、スクリーンリーダーのユーザーが読み上げさせたものが、意味をなすことでしょう。

### UI コントロール

ここで UI コントロールという言葉によって意味しているのは、ユーザーが対話的に操作する対象の、ウェブドキュメントの主要部分のことであり、もっとも一般的には、ボタン、リンク、およびフォーム・コントロールのことです。本節では、そうしたコントロールを作る際に認識しておくべき基本的なアクセシビリティの問題を見てゆきましょう。WAI-ARIA とマルチメディアに関する後続の記事で、UI アクセシビリティの他の側面について見ることにします。

UI コントロールのアクセシビリティに対する一つの重要な側面は、ブラウザーがデフォルトでは 、UI コントロールをキーボードで操作できるようにしている、ということです。このことは、[native-keyboard-accessibility.html](http://mdn.github.io/learning-area/tools-testing/cross-browser-testing/accessibility/native-keyboard-accessibility.html) の例 ([ソースコード](https://github.com/mdn/learning-area/blob/master/tools-testing/cross-browser-testing/accessibility/native-keyboard-accessibility.html) を参照) を用いて試せます。これを新規タブで開いて、タブキーを押してみてください。二、三回押してみた後には、フォーカス可能な異なる要素の間をタブ・フォーカスが動き回り始めたのだと分かるはずです。どの要素にフォーカスが当たっているのかが分かるように、どのブラウザーでも、フォーカスの当たっている要素には、ハイライトされたデフォルトのスタイルが付与されます (そのスタイルは、異なるブラウザー間では少し差があります)。

![](button-focused-unfocused.png)

その後、エンターキー / リターンキーを押すと、フォーカスの当たっているリンクをたどることもできますし、または、ボタンを押すこともできますし (ボタンにメッセージ警告を出させるための JavaScript を含めておきました)、あるいは、テキスト入力欄にテキストを入力するためのタイピングを開始することもできます (他のフォーム要素には別のコントロールがあります。たとえば、{{htmlelement("select")}} 要素は、選択肢を表示させることや、上下の矢印キーを用いて選択肢の間を行ったり来たりさせることができます)。

> **Note:** 異なるブラウザーでは、異なるキーボード・コントロール・オプションを使用可能としている場合があります。さらに詳しいことは、[Using native keyboard accessibility](/ja/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#Using_native_keyboard_accessibility) を参照してください。

こうした振る舞いは、たとえば以下のように単に適切な要素を用いるだけで、本質的にはただで手に入ります。

```html example-good
<h1>Links</h1>

<p>This is a link to <a href="https://www.mozilla.org">Mozilla</a>.</p>

<p>Another link, to the <a href="https://developer.mozilla.org">Mozilla Developer Network</a>.</p>

<h2>Buttons</h2>

<p>
  <button data-message="This is from the first button">Click me!</button>
  <button data-message="This is from the second button">Click me too!</button>
  <button data-message="This is from the third button">And me!</button>
</p>

<h2>Form</h2>

<form>
  <div>
    <label for="name">Fill in your name:</label>
    <input type="text" id="name" name="name">
  </div>
  <div>
    <label for="age">Enter your age:</label>
    <input type="text" id="age" name="age">
  </div>
  <div>
    <label for="mood">Choose your mood:</label>
    <select id="mood" name="mood">
      <option>Happy</option>
      <option>Sad</option>
      <option>Angry</option>
      <option>Worried</option>
    </select>
  </div>
</form>
```

これは、リンクやボタンやフォーム要素やラベルを適切に用いることを意味しています (フォーム・コントロール用の {{htmlelement("label")}} 要素を含めています)。

しかし、またしてもですが、人が HTML で変なことをする場合がときにはあるものです。たとえば、次のように {{htmlelement("div")}} を用いてマークアップしたボタンを見かけることも、ときにはあります。

```html example-bad
<div data-message="This is from the first button">Click me!</div>
<div data-message="This is from the second button">Click me too!</div>
<div data-message="This is from the third button">And me!</div>
```

しかし、そうしたコードを使うことは、勧められることではありません。単に {{htmlelement("button")}} 要素を使っていたなら得られていたはずの、ネイティブなキーボード・アクセシビリティを直ちに失ってしまううえに、当該ボタンが得るデフォルトの CSS スタイル付けを何も得られないからです。

#### キーボード・アクセシビリティを呼び戻すように盛り込む

そうした利点を呼び戻すように追加するには、ちょっとした作業が必要です ([fake-div-buttons.html](http://mdn.github.io/learning-area/tools-testing/cross-browser-testing/accessibility/fake-div-buttons.html) で例示的コードを試せます。[ソースコード](https://github.com/mdn/learning-area/blob/master/tools-testing/cross-browser-testing/accessibility/fake-div-buttons.html) も参照してください)。ここでは、各ボタンに `tabindex="0"` という属性を付与することによって、見せかけの `<div>` ボタンにフォーカスを当てられるようにしました (タブキーを通じてのフォーカスを含みます)。

```html
<div data-message="This is from the first button" tabindex="0">Click me!</div>
<div data-message="This is from the second button" tabindex="0">Click me too!</div>
<div data-message="This is from the third button" tabindex="0">And me!</div>
```

基本的には、{{htmlattrxref("tabindex")}} 属性は、タブキーでの移動が可能な要素に、単なるデフォルトのソース順でのタブ移動の代わりとなる特別あつらえのタブ順序 (正数の順で指定されるもの) を持たせられるようにすることを、主に意図したものです。これはほとんどの場合、筋の悪い考え方です。なぜなら、重大な混乱を招きかねないからです。本当に必要な場合にのみ、{{htmlattrxref("tabindex")}} 属性を使うようにしてください。たとえば、レイアウトによって、物事がソースコードとはまるで違った見かけ上の順序で示されており、かつ、より論理的に物事を機能させたいと望んでいるような場合です。`tabindex` には、あと二つの選択肢があります。

- `tabindex="0"` — 上記のとおり、この値によって、普通ならタブキーでの移動が可能ではない要素が、タブキーでの移動が可能となります。これは、`tabindex` の一番有益な値です。
- `tabindex="-1"` — これによって、普通ならタブキーでの移動が可能ではない要素が、(たとえば JavaScript を介して) プログラム的にフォーカスを得たり、あるいはリンクのターゲットとしてフォーカスを得たりすることが可能となります。

上記のような追加作業によって、タブキーでボタンに移動できるようにはなりますが、エンターキー / リターンキーを介してボタンをアクティブにすることはできるようになりません。それを可能とするには、以下のようなちょっとした JavaScript のごまかしを追加せねばなりません。

```js
document.onkeydown = function(e) {
  if(e.keyCode === 13) { // The Enter/Return key
    document.activeElement.onclick(e);
  }
};
```

ここでは、キーボード上でいつボタンが押されたのかを検出するために、`document` オブジェクトにリスナーを追加しています。どのボタンが押されたのかを、イベント・オブジェクトの [`keyCode`](/ja/docs/Web/API/KeyboardEvent/keyCode) プロパティを介して調べています。 \[訳注: 以上の二つの文の「ボタン」はキーボード上のキーのことのようです。また、`keyCode` プロパティは非推奨になっています。]もしエンターキー / リターンキーに合致するキーコードだったら、`document.activeElement.onclick()` を用い、ボタンの `onclick` ハンドラーに記憶されている関数を実行します \[訳注: この文の「ボタン」は `<div>` ボタンのことのようです]。[`activeElement`](/ja/docs/Web/API/Document/activeElement) は、ページ上で現在フォーカスの当たっている要素を教えてくれます。

> **Note:** 自分の独自のイベントハンドラーを、イベントハンドラー・プロパティ (たとえば `onclick`) を介して設定した場合にのみ、この技法がうまくいくだろうということに留意すべきです。`addEventListener` だと、うまくいきません。

これでは、機能を呼び戻すように盛り込むための、余計な厄介ごとの山ですね。それに、これにともなう他の問題もきっとあるはずです。**そもそも、単にふさわしい要素をふさわしい役割に使うべきなのです。**

#### 意味の通るテキストラベル

UI コントロールのテキストラベルはあらゆるユーザーにとって大変有益ですが、そうしたラベルを適切なものにしておくことは、とりわけ、障碍のあるユーザーにとって重要です。

ボタンとリンクテキストのラベルが、理解可能であり、かつ弁別性のあるものになっていることを、確認すべきです。ラベルとして単に「ここをクリック」を使うのはいけません。なぜなら、スクリーンリーダーのユーザーは、ボタンとフォーム・コントロールの一覧をまとめ上げることがあるからです。以下のスクリーンショットは、Mac 上の VoiceOver によって一覧化されたコントロールを示しています。

![](voiceover-formcontrols.png)

ラベルが存在している段落の文脈内においてラベルが意味をなすようにするだけでなく、文脈を離れてもラベルが意味をなすように (ラベルが単独で読まれても意味をなすように) してください。たとえば、以下のものは、良いリンクテキストの例を示しています。

```html example-good
<p>クジラは本当にすごい生き物です。<a href="whales.html">クジラについてもっと知ってくださいね</a>。</p>
```

しかしこれは駄目なリンクテキストです。

```html example-bad
<p>クジラは本当にすごい生き物です。クジラについてもっと知るには、<a href="whales.html">ここをクリックしてください</a>。</p>
```

> **Note:** リンクの実装とベスト・プラクティスに関するさらなる情報を、[Creating hyperlinks](/ja/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks) という記事で知ることができます。また、いくつかの良い例と悪い例を、[good-links.html](http://mdn.github.io/learning-area/accessibility/html/good-links.html) と [bad-links.html](http://mdn.github.io/learning-area/accessibility/html/bad-links.html) で見ることもできます。

フォーム・ラベルも重要です。なぜなら、各フォーム入力欄に何を入力する必要があるのかについての手がかりを与えてくれるからです。以下のものは、十分に筋の通った例のように見えます。

```html example-bad
名前を入れてください: <input type="text" id="name" name="name">
```

しかしこれは、障碍のあるユーザーにとって、それほど有用ではありません。このラベルを曖昧性なしにフォーム入力欄に結びつけ、そして、仮に入力欄が見えなくても、入力欄をどう埋めたら良いのかを明確にしてくれるものが、上記の例には何もありません。なんらかのスクリーンリーダーでこの例にアクセスした場合には、「テキストを編集する」のような感じの説明のみが与えられることもあるかもしれません。

以下のものは、ずっと良い例です。

```html example-good
<div>
  <label for="name">名前を入れてください:</label>
  <input type="text" id="name" name="name">
</div>
```

このようなコードだと、ラベルが明確に入力欄と結びつけられることになります。説明は、(上記のような単なる「テキストを編集する」ではなくて) むしろ「名前を入れてください: テキストを編集する」といった感じのものになるでしょう。

![](voiceover-good-form-label.png)

追加のおまけとして、ほとんどのブラウザーにおいて、ラベルをフォーム入力欄に結びつけることは、ラベルをクリックして当該フォーム要素を選択 / アクティブ化することが可能なことを意味します。このことにより、入力欄に対して、より大きなヒット領域を与えることになり、したがって、入力欄が選択しやすくなります。

> **Note:** [good-form.html](http://mdn.github.io/learning-area/accessibility/html/good-form.html) と [bad-form.html](http://mdn.github.io/learning-area/accessibility/html/bad-form.html) で、いくつかの良いフォーム例と悪いフォーム例を見られます。

## アクセシブルなデータテーブル

基本的なデータテーブルは、たとえば以下のように、とても簡素なマークアップで書けます。

```html
<table>
  <tr>
    <td>Name</td>
    <td>Age</td>
    <td>Gender</td>
  </tr>
  <tr>
    <td>Gabriel</td>
    <td>13</td>
    <td>Male</td>
  </tr>
  <tr>
    <td>Elva</td>
    <td>8</td>
    <td>Female</td>
  </tr>
  <tr>
    <td>Freida</td>
    <td>5</td>
    <td>Female</td>
  </tr>
</table>
```

しかしこれには問題があります。スクリーンリーダーのユーザーには、行または列をデータの集まりとしてまとめて関連づける手段が何もないのです。こうした関連づけを行うには、見出し行がどれなのか、見出し行は複数の行を統率しているのか、複数の列を統率しているのか、などといったことを知らねばなりません。こうしたことは、上記のテーブルでは、視覚的に行われる以外にありません ([bad-table.html](http://mdn.github.io/learning-area/accessibility/html/bad-table.html) を参照して、その例をご自分で試してみてください)。

では、 [パンクバンドのテーブルの例](https://github.com/mdn/learning-area/blob/master/css/styling-boxes/styling-tables/punk-bands-complete.html) を見てみましょう。ここでは、多少のアクセシビリティ支援が機能していることが分かりますね。

- テーブルの見出しは、 {{htmlelement("th")}} 要素を用いて定義されています。さらに、`scope` 属性を使って、その見出しが行に対する見出しなのか列に対する見出しなのかを指定することもできます。こうすると、スクリーンリーダーが一つの単位として処理できる、データの完全なグループが示されることになります。
- {{htmlelement("caption")}} 要素と、`<table>` の `summary` 属性は、どちらも似たような役割を果たします。テーブルに対する alt テキストとして機能し、スクリーンリーダーのユーザーに対して、テーブルの中身についての有用で手短な要約を示すのです。`<caption>` が一般に好ましいのですが、それは、晴眼者のユーザーに対しても `<caption>` の中身がアクセシブルだからであり、晴眼者のユーザーもその中身を有用だと思うでしょう。実際には、(必ずしも) 二つとも必要というわけではありません。

> **Note:** アクセシブルなデータテーブルにまつわる更なる詳細は、[HTML テーブルの発展的な機能とアクセシビリティ](/ja/docs/Learn/HTML/Tables/Advanced) という記事を参照してください。

## 代替テキスト

テキストによるコンテンツは本質的にアクセシブルですが、マルチメディア・コンテンツについては必ずしも同じことが言えるわけではありません。画像 / 動画コンテンツは視覚障碍者には見えず、音声コンテンツは聴覚障碍者には聞こえません。動画と音声のコンテンツについては、[アクセシブルなマルチメディア](/ja/docs/Learn/Accessibility/Multimedia) という記事で後に詳しく扱うことにしますが、本記事では、ごく普通の {{htmlelement("img")}} 要素についてのアクセシビリティを見てゆきましょう。

[accessible-image.html](http://mdn.github.io/learning-area/accessibility/html/accessible-image.html) という簡単な例を書き上げました。これは、4 枚の同じ画像を含んでいます。

```
<img src="dinosaur.png">

<img src="dinosaur.png"
     alt="A red Tyrannosaurus Rex: A two legged dinosaur standing upright like a human, with small arms, and a large head with lots of sharp teeth.">
<!--
[alt 属性の訳: 赤いティラノサウルス・レックス。人間のように直立する二足歩行の恐竜で、腕は小さく、頭部は大きくて多くの鋭い歯があります。]
-->

<img src="dinosaur.png"
     alt="A red Tyrannosaurus Rex: A two legged dinosaur standing upright like a human, with small arms, and a large head with lots of sharp teeth."
     title="The Mozilla red dinosaur">
<!--
[alt 属性の訳: 赤いティラノサウルス・レックス。人間のように直立する二足歩行の恐竜で、腕は小さく、頭部は大きくて多くの鋭い歯があります。]
[title 属性の訳: Mozilla の赤い恐竜]
-->

<img src="dinosaur.png" aria-labelledby="dino-label">

<p id="dino-label">The Mozilla red Tyrannosaurus Rex: A two legged dinosaur standing upright like a human, with small arms, and a large head with lots of sharp teeth.</p>
<!--
[p 要素の中身の訳: Mozilla の赤いティラノサウルス・レックス。人間のように直立する二足歩行の恐竜で、腕は小さく、頭部は大きくて多くの鋭い歯があります。]
-->
```

1 枚目の画像は、スクリーンリーダーで見たときに、実際のところ大した手助けをユーザーに与えてはくれません。たとえば VoiceOver は、「/dinosaur.png, image」と読み上げます。なんらかの手助けを提供しようとしてファイル名を読み上げるわけです。この例では、ユーザーは、少なくともこれがある種の恐竜なのだと知ることでしょうが、機械で生成されたファイル名とともにファイルが (たとえばディジタルカメラから) アップロードされる場合もよくありますし、そうしたファイル名は画像の中身に対する文脈を何も与えてはくれないでしょう。

> **Note:** これこそが、画像の内部にテキストコンテンツを決して含めるべきではない理由です。スクリーンリーダーは、まったくそのテキストコンテンツにアクセスできません。それに、他の欠点もあります。すなわち、そのテキストコンテンツを選択することもコピー / ペーストすることもできません。画像の内部にテキストコンテンツを含めるなどということは、とにかくしないでください!

スクリーンリーダーは、2 枚目の画像に出くわすと、alt 属性を丸々読み上げます。つまり、「赤いティラノサウルス・レックス。人間のように直立する二足歩行の恐竜で、腕は小さく、頭部は大きくて多くの鋭い歯があります」と読み上げます。

この例は、いわゆる **alt テキスト**が万一使えない場合に備えて意味のあるファイル名を使うことだけでなく、可能な場合にはいつでも alt テキストを `alt` 属性において確実に提供しておくことの重要性を、際立たせるものです。`alt` 属性の中身は常に、画像の端的な描写と、画像が視覚的に伝えているものとを提供すべきであることに、注意してください。ここには、個人的な知識や追加的な説明を何も含めるべきではありません。なぜなら、以前にその画像に出くわしたことのない人にとって有益ではないからです。

考えるべきことの一つは、画像がコンテンツの内部で意味を持っているのか、あるいは、純粋に視覚的装飾のためのものであって意味は持たないのか、ということです。もし画像が装飾用であれば、その画像を CSS 背景画像としてページ内に含めるだけにする方が良いのです。

> **Note:** 画像の実装とベスト・プラクティスについての更なる多くの情報については、[Images in HTML](/ja/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML) と [Responsive images](/ja/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images) をお読みください。

文脈のある追加的な情報をどうしても提示したい場合、その情報は、画像の周囲のテキストの中か、あるいは、上記のように `title` 属性の内部に入れるべきです。この場合、ほとんどのスクリーンリーダーは、`alt` テキストと、`title` 属性と、ファイル名とを読み上げるでしょう。さらに、マウスオーバーしたときには、ブラウザーが `title` テキストをツールチップとして表示します。

![](title-attribute.png)

4 番目の方法についてもざっと見ておきましょう。

```html
<img src="dinosaur.png" aria-labelledby="dino-label">

<p id="dino-label">The Mozilla red Tyrannosaurus ... </p>
```

この場合、`alt` 属性をまったく使っていません。その代わり、画像についての説明を通常のテキスト段落として提示し、その段落に `id` を与え、そして、その `id` を参照するための `aria-labelledby` 属性を用いました。こうすると、スクリーンリーダーに、その段落をその画像についての alt テキスト / ラベルとして使わせることになります。これは、複数の画像に対して同じテキストをラベルとして使いたい場合に、とりわけ有用です (こうしたことは、`alt` を使ってではできない事柄なのです)。

> **Note:** `aria-labelledby` は [WAI-ARIA](https://www.w3.org/TR/wai-aria-1.1/) 仕様の一部です。これのおかげで開発者は、必要な箇所においてスクリーンリーダーのアクセシビリティを高めるために、自分のマークアップに追加的な意味 (セマンティクス) を足すことができます。これがどのように機能するのかについての更なる情報を知るには、[WAI-ARIA の基本](/ja/docs/Learn/Accessibility/WAI-ARIA_basics) の記事をお読みください。

### その他の代替テキストの仕組み

画像には、説明的テキストを提供するのに利用可能な別の仕組みもあります。たとえば、画像についての広範囲にわたる説明を含む別のウェブドキュメントを指すことを意図した、`longdesc` 属性があります。たとえば以下のようなものです。

```html
<img src="dinosaur.png" longdesc="dino-info.html">
```

これは良い考えのように思えます。というのも、とりわけ、多くの情報が載っている大きな図表のようなインフォグラフィックを、代わりにアクセシブルなデータテーブル (前節を参照) として表現することがおそらくは可能でしょうから。しかし、`longdesc` は、スクリーンリーダーによっていつもサポートされているわけではありませんし、スクリーンリーダー以外のものを使っているユーザーにとっては、コンテンツがまったくアクセス不能です。まず間違いなく、画像と同じページに長い説明を含めるか、あるいは、通常のリンクを使って長い説明にリンクする方が、ずっと良いのです。

HTML5 は、{{htmlelement("figure")}} と {{htmlelement("figcaption")}} という二つの新規要素を含みます。これらは、なんらかの種類の図面 (任意のものであってよく、必ずしも画像とは限りません) を、図面キャプション (説明文) と結びつけることになっているものです。

```html
<figure>
  <img src="dinosaur.png" alt="Mozilla のティラノサウルス">
  <figcaption>赤いティラノサウルス・レックス。人間のように直立する二足歩行の恐竜で、腕は小さく、頭部は大きくて多くの鋭い歯があります。</figcaption>
</figure>
```

あいにく、ほとんどのスクリーンリーダーは、まだ、図面キャプションを図面と結びつけてはくれないようです。ですが、この要素構造は CSS でのスタイルづけにとって有益ですし、ソース内で画像の隣にその画像の説明を配置するための手段を与えてもくれます。

### 空の代替テキスト

```html
<h3>
  <img src="article-icon.png" alt="">
  ティラノサウルス・レックス: 恐竜の王
</h3>
```

画像がページのデザインに含まれるけれども、主目的は視覚的装飾である、といった場合もあるかもしれません。上記のコード例において、画像の `alt` 属性が空であることにお気づきでしょう。これは、スクリーンリーダーに画像を認識させるものですが、その画像を説明しようとさせるものではありません (説明する代わりに、スクリーンリーダーは、単に「画像」とか何とか言うでしょう)。

`alt` を含めないようにする代わりに空の `alt` を用いる理由は、`alt` が与えられていない場合には多くのスクリーンリーダーが画像の URL を丸々全部発声するからです。上記の例において画像は、その画像が結びつけられている見出しに対する視覚的装飾として機能しています。このような場合、および、画像が単に装飾にすぎず中身の価値がない場合には、画像に空の `alt` を入れるべきです。別の選択肢は、`role="presentation"` という ARIA `role` 属性を使うことです。こうすることによっても、スクリーンリーダーに代替テキスト (`alt` テキスト) を読み上げるのをやめさせることができます。

> **Note:** もし可能なら、単なる修飾であるような画像を表示するのには CSS を使うべきです。

## 要約

今や読者の皆さんは、ほとんどの場合にアクセシブルな HTML を書くことについて、熟知しているはずです。[WAI-ARIA の基本](/ja/docs/Learn/Accessibility/WAI-ARIA_basics) の記事も、この知識の抜けを埋めてくれるでしょうが、本記事でもその基本には気を配ってきました。次は、CSS と JavaScript を検討しましょう。そして、CSS と JavaScript の良い使い方やまずい使い方によって、アクセシビリティがどのような影響を受けるのかを検討しましょう。

{{PreviousMenuNext("Learn/Accessibility/What_is_Accessibility","Learn/Accessibility/CSS_and_JavaScript", "Learn/Accessibility")}}

## このモジュール内

- [アクセシビリティとは?](/ja/docs/Learn/Accessibility/What_is_accessibility)
- [HTML: アクセシビリティの基礎](/ja/docs/Learn/Accessibility/HTML)
- [CSS と JavaScript のアクセシビリティのベスト・プラクティス](/ja/docs/Learn/Accessibility/CSS_and_JavaScript)
- [WAI-ARIA の基本](/ja/docs/Learn/Accessibility/WAI-ARIA_basics)
- [アクセシブルなマルチメディア](/ja/docs/Learn/Accessibility/Multimedia)
- [モバイルアクセシビリティ](/ja/docs/Learn/Accessibility/Mobile)
- [アクセシビリティのトラブルシューティング](/ja/docs/Learn/Accessibility/Accessibility_troubleshooting)
