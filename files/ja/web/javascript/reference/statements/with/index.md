---
title: with
slug: Web/JavaScript/Reference/Statements/with
---

> **Warning:** 混乱させるバグや互換性問題の原因になり得るため、`with` 文の使用は推奨されません。詳しくは "説明" の章の "あいまい性の欠点" をご覧ください。

{{jsSidebar("Statements")}}

**with 文**は、文に対するスコープチェーンを拡張します。

## 構文

```
with (expression)
  statement
```

- `expression`
  - : 文を評価するときに使われるスコープチェーンに、与えられたオブジェクトを追加します。オブジェクトの周りの括弧は必須です。
- `statement`
  - : 任意の文。複数の文を実行するためには、それらの文をグループ化するために[ブロック](/ja/docs/Web/JavaScript/Reference/Statements/block)文 ({ ... }) を使ってください。

## 解説

JavaScript は、スクリプトの実行コンテキストまたは非修飾名を含む関数の実行コンテキストに関連付けられたスコープチェーンを探索することにより、非修飾名を探します。 'with' 文は、その文本体の評価の間、このスコープチェーンの先頭に、与えられたオブジェクトを追加します。もし本体で使われた非修飾名がそのスコープチェーンの中のプロパティに一致するなら、その名前はそのプロパティとそのプロパティを含むオブジェクトとに結び付けられます。そうでなければ、 {{jsxref("ReferenceError")}} が発生します。

> **Note:** `with` の利用は非推奨であり、ECMAScript 5 の[厳格モード](/ja/docs/Web/JavaScript/Reference/Functions_and_function_scope/Strict_mode)では禁止されています。推奨される代替案は、参照したいプロパティを持つオブジェクトを一時変数に代入することです。

### 性能上の利点と欠点

**利点:** `with` 文 は、性能の悪化なしに、長ったらしいオブジェクトの参照を繰り返す必要性を減らすことにより、ファイルサイズの削減に役立ちます。'with' 文 により必要とされるスコープチェーンの変更は、計算コストが高いものではありません。'with' 文 の使用は、インタープリターが、繰り返されるオブジェクトの参照を解析するのを楽にするでしょう。しかしながら、多くの場合では、これによる利益は、望むオブジェクトへの参照を保存するための一時的な変数を使うことにより達成されるということに注意してください。

**欠点:** `with` 文 は、すべての非修飾名の検索に対して、指定されたオブジェクトが最初に探索されることを強制します。それゆえに、関数の仮引数および宣言されたローカル変数名に一致するすべての識別子は、'with' 文 ブロックの中では見つかるのがより遅くなるでしょう。性能が重要な場所では、'with' 文 は、関数の引数および宣言されたローカル変数の識別子を使わないコードブロックを包み込むためだけに使われるのが適切でしょう。

### あいまい性の欠点

**欠点:** `with` 文 は、非修飾名がスコープチェーンの中で見つかるかどうか、もし見つかるならどのオブジェクトの中でかを、人間の読み手または JavaScript コンパイラーが決定するのを難しくします。つまり、以下の例を見てください。

```js
function f(x, o) {
  with (o) {
    console.log(x);
  }
}
```

`f` が呼び出されたときのみ、`x` が見つかるかどうか、もし見つかるなら、`o` の中でか、または (そのようなプロパティが存在しなければ) `f` のアクティベーションオブジェクト――そこで、`x` は最初の仮引数の名前です――の中でか、が決定されます。もし第 2 引数として渡したオブジェクトの中で `x` を定義するのを忘れた、または何らかの似たようなバグあるいは混乱があったのなら、エラーが起きることなく、ただ予期しない結果が得られるでしょう。

**欠点:** `with` を使用したコードは前方互換性がない可能性があります。普通のオブジェクト以外のものと使用した場合に顕著です。以下の例で考えましょう。

```js
function f(foo, values) {
  with (foo) {
    console.log(values);
  }
}
```

ECMAScript 5 環境で `f([1,2,3], obj)` を呼び出すと、`with` 文の中にある `values` の参照先は `obj` に解決されます。ところが、ECMAScript 2015 では {{jsxref("Array.prototype")}} に `values` プロパティが導入されました (よって、すべての配列で使用できます)。従って ECMAScript 2015 に対応する JavaScript 環境では、 `with` 文の内部にある `values` の参照先は `[1,2,3].values` になります。ただし、この例に限って言えば、 {{jsxref("Array.prototype")}} では `values` が {{jsxref("Symbol.unscopables")}} オブジェクトの中に定義されています。もしそうでなければ、デバッグが困難な問題であることがわかります。

## 例

### with の使用

次の `with` 文は、 {{jsxref("Math")}} オブジェクトが既定のオブジェクトであると指定しています。`with` 文内の複数の文は、オブジェクトを指定することなく、 {{jsxref("Math.PI", "PI")}} プロパティ、 {{jsxref("Math.cos", "cos")}} メソッド、および {{jsxref("Math.sin", "sin")}} メソッドを参照しています。JavaScript は、これらの参照に対して `Math` オブジェクトを仮定します。

```js
var a, x, y;
var r = 10;

with (Math) {
  a = PI * r * r;
  x = r * cos(PI);
  y = r * sin(PI / 2);
}
```

## 仕様書

| 仕様書                                                                               |
| ------------------------------------------------------------------------------------ |
| {{SpecName('ESDraft', '#sec-with-statement', 'with statement')}} |

## ブラウザーの互換性

{{Compat("javascript.statements.with")}}

## 関連情報

- {{jsxref("Statements/block", "block", "", 1)}}
- [厳格モード](/ja/docs/Web/JavaScript/Reference/Functions_and_function_scope/Strict_mode)
- {{jsxref("Symbol.unscopables")}}
- {{jsxref("Array.@@unscopables", "Array.prototype[@@unscopables]")}}
