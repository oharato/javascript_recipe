---
layout: default
---
JavaScript逆引きレシピで勉強する

# 01 基本構文

## 001 HTMLページにJavaScriptのコードを組み込みたい

```
<body>

<script type="text/javascript">
console.log('hoge');
</script>
</body>
```

- body閉じタグの直前がおすすめ

```
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

## 010 数値型の値を表現したい

```
var num = 0xFF // 16進数リテラル(255)
var num = 1.5e-3 // 浮動小数点リテラル(0.0015)
```

## 011 真偽値

## 012 配列
- リテラル表現

```
var data = ['a', 'b', 'c']
```

- 参照はブラケット構文

```
data[0] // 'a'
```

## 013 連想配列(ハッシュ)
- Objectオブジェクトを連想配列として利用。連想配列のキーをプロパティ、値として関数リテラルを持つプロパティのことをメソッド。
- リテラル表現

```
var obj1 = {a:100, b:200, c:300}
```

- Objectコンストラクタ

```
var obj2 = new Object();
obj2.a = 100;
obj2.b = 200;
obj2.c = 300;
```

- 値を参照するにはドット演算子(キーは識別子のみ。数字不可)かブラケット構文

```
var obj = {a:100, 2:'hoge'}
obj.a
100
obj.2
SyntaxError: missing ; before statement
obj[a]
ReferenceError: a is not defined
obj['a']
100
obj[2]
"hoge"
```

## 014 データ型を変換したい
- 数値型へ

```
parseInt('888abc') // 888
parseFloat('888abc') // 888
Number('888abc') // NaN

parseInt('0x10') // 16
parseFloat('0x10') // 0
Number('0x10') // 16

parseInt('1.414E3') // 1
parseFloat('1.414E3') // 1414
Number('1.414E3') // 1414
```

- 文字列型、論理型へ
    - Boolean関数は、空文字、ゼロ、NaN、null、undefinedをfalse、それ以外をtrue

```
String(123) // '123'
Boolean(-1) // true
```


{% gist oharato/bef63fca2dde79d27f2e %}