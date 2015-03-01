---
layout: default
---
JavaScript逆引きレシピで勉強する

# 01 基本構文
## 001 HTMLページにJavaScriptのコードを組み込みたい
```HTML
<body>

<script type="text/javascript">
console.log('hoge');
</script>
</body>
```
- body閉じタグの直前がおすすめ

```HTML
<!-- 外部スクリプト -->
<script src="http://code.jquery.com/jquery-1.11.0.min.js"></script>
<!-- インラインスクリプト -->
<script type="text/javascript">
$(function(){
  $('#mem').css('background-color', '#ff6');
});
</script>
```

## 002 JavaScriptの基礎文法
- 文の末尾はセミコロン
- 複数の文を1行にまとめない（デバッグしにくい）

## 003 JavaScriptのコメント
- ```/*～*/```よりも```//```を優先して使う

## 004 コメントから仕様書を作成
- JSDocを使う

## 005 JavaScriptの危険な構文を取り除く
- Strictモードを使う

|分類|制限内容|
|:-|:-|
|変数|varは省略できない、引数やプロパティ名の重複禁止、undefinedなどへの代入禁止|
|命令|with使用不可など|
|その他|関数配下のthisはGlobalオブジェクトを示さない(undefined)|

- 使い方
スクリプトや関数の先頭に下記を追加
```
'use strict;'
```

## 006 JavaScriptのコードを圧縮
- オンラインだとCompressor
- オフラインだとMicrosoft Ajax Minifier

## 007 変数
- 必ずvarで宣言
```
var msg = 'hoge';
```

- クラスはPascalで(MyApp)、変数と関数はcamelcaseで(myApp)

## 008 文字列
- タグの属性はダブルクォートで括るのが多いのでシングルクォートがおすすめ
```
var tag = '<img src="hoge.png" />';
```

## 009 文字列の中で改行やタブ
```
'hoge\nfuga'
'\thoge'
```