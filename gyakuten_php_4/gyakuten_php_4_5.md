---
title: "gyakuten_php_4_5"
tags: ""
---
## foreach文

繰り返し処理は、何度も同じ処理を繰り返したい時に使用するものです。

これまで`for`や`while`を学習してきてきましたが、今回は現場でもかなり使われている`foreach`について勉強していきましょう。
（実際の現場では`for`や`while`はあまり使われないと思って差し支えありません）

### foreachとは

`foreach`は配列や範囲オブジェクトに対して使用することができる繰り返し処理です。ちなみに、配列（連想配列）とは何個も要素を格納することができるもので、範囲オブジェクトとは0~100のように、数値的な範囲を表すデータのことです。

それではさっそく、`foreach`の使い方を確認していきましょう。以下のようにコードを記述してください。

```php
<?php
    
// 配列 複数のデータを格納できる
$users = ["satou", "tanaka", "yamada", "shimizu"];

// 配列に対してforeach文で中身を表示
// $usersの要素１つ１つを$userに代入してブロック内の処理を実行
foreach($users as $name){
  echo "Hello!!".$user;
}

?>
```

#### 実行結果

    Hello!! satou
    Hello!! tanaka
    Hello!! yamada
    Hello!! shimizu

はじめて`foreach`を見る人なら混乱するかと思います。落ち着いて、1つ1つ確認しながら進めていきましょう。

まず、`foreach`のこの部分から。

```php
foreach($users as $user) {
  // 行いたい処理
}
```

上の中で`$users`は複数の要素が入った配列になります。その配列に対して`foreach`を実行することによって、要素を1つ1つ取り出して処理を行うことができるわけです。

で、そのときに大切になってくるのが配列から取り出された各要素が`as`の後に記述している`$user`に代入されることです。

まとめると、配列の`$users`に対して`foreach`を使用すると、1つ1つの要素が`$user`に代入され、`{`}と`}`で囲まれた部分の処理が実行されるということになります。

この`foreach`については、構文がわりと複雑なので理解がしにくいかと思いますが、いろんなサンプルを書いて実行し、`foreach`を書くことに慣れていきましょう。

```php
<?php
    
$ages = [20, 60, 27, 23];

foreach($ages as $age) {
  echo "I'm ".$age. "years old.";
}


$items = ["book", "food", "movie", "music"];

foreach($items as $item) {
  echo "I bought ".$item;
}


$prefectures = ["Hokkaido", "Okinawa", "Saitama", "Ibaraki"];

foreach($prefectures as $prefecture) {
  echo $prefecture." is awesome!!";
}

?>
```

### foreach(連想配列 as $key => $value)

先程までは`foreach`を使って、配列の各要素に対して1つずつ繰り返し処理を実行するコードを書いてきましたが、連想配列に対しても1つずつ繰り返し処理を実行できるコードを書いていきましょう。

```php
<?php

$users = [
    1 => "satou",
    2 => "tanaka",
    3 => "yamada",
    4 => "shimizu"];

# インデックス番号と配列の要素を同時に出力
foreach($users as $key => $value){
  echo "No.".$key."は".$value."です";
}
    
?>
```

#### 実行結果

    No.0はsatouです
    No.1はtanakaです
    No.2はyamadaです
    No.3はshimizuです

実行結果のように、連想配列に対して`foreach`を利用すると、インデックス（`$key`）と値（`$value`）を1つずつ取り出して繰り返し処理を実行することができます。

`foreach`を連想配列に対して使用する場合、`$key`と`$value`の名前は自由に変えることができます。

例えば、以下のように書くことができます。

```php
<?php
    
$fruitesPrices = [
	'apple' => 150,
	'banana' => 100,
	'orange' => 200,
	'peach' => 300
];

foreach($fruitesPrices as $frute => $price){
    echo $fruite."の値段：".$price."円";
}
    
?>
```

#### 実行結果

    appleの値段：150円
    bananaの値段：100円
    orangeの値段：200円
    peachの値段：300円

今回は`$key`を`fruite`に、`value`を`price`に変えました。現場でも変数名はできるだけ一目で内容がわかるように命名されるのでぜひ、命名の練習もしておきましょう。

また、連想配列は`[ ]`で書きましたが、`array( )`で書いても構いません。

多くのプログラミング教材では`array( )`が紹介されていますが、現場では`[ ]`の方が多く使われているので`[ ]`も使ってみてください。

\###まとめ
`PHP`では、繰り返し処理には`foreach`をよく利用します。実際の現場でも`foreach`は`for`や`while`に比べ、かなりの頻度で登場しますのでぜひマスターしてください。

ですので`for`や`while`はさらっと把握して`foreach`の重点的にマスターしてください。

できるだけ、無駄を省きながら効率よく勉強されていくと、転職のスピードも早くなるかと思います。ぜひ、ショートカットしながら勉強を進めて行ってください。

お疲れ様でした！
