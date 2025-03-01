---
title: Storage.removeItem()
slug: Web/API/Storage/removeItem
---
{{APIRef("Web Storage API")}}

{{domxref("Storage")}} インターフェイスの **`removeItem()`** メソッドは、キーの名称を渡すと、指定された `Storage` からキーを削除します。指定されたキーに関連付けられた項目がない場合、このメソッドは何もしません。

## 構文

```
storage.removeItem(keyName);
```

### 引数

- `keyName`
  - : 削除したいキーの名称を持つ {{domxref("DOMString")}}。

### 返値

{{jsxref("undefined")}}。

## 例

以下の関数はローカルストレージに 3 個のデータ項目を作成して、 `image` データ項目を削除します。

```js
function populateStorage() {
  localStorage.setItem('bgcolor', 'red');
  localStorage.setItem('font', 'Helvetica');
  localStorage.setItem('image', 'myCat.png');

  localStorage.removeItem('image');
}
```

> **Note:**  実際の例として、 [Web Storage Demo](https://mdn.github.io/dom-examples/web-storage/) をご覧ください。

## 仕様書

| 仕様書                                                                                                                   | 状態                             | 備考 |
| ------------------------------------------------------------------------------------------------------------------------ | -------------------------------- | ---- |
| {{SpecName('HTML WHATWG', 'webstorage.html#dom-storage-removeitem', 'Storage.removeItem')}} | {{Spec2('HTML WHATWG')}} |      |

## ブラウザーの対応

{{Compat("api.Storage.removeItem")}}

## 関連情報

[Web Storage API の使用](/ja/docs/Web/API/Web_Storage_API/Using_the_Web_Storage_API)
