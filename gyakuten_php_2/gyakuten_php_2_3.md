### AかつB

条件分岐の条件で`AかつB`を設定するためには`&&`を使います。

それでは、以下の名前のファイル名を作成しましょう。（index.phpを上書きしても構いません）

    and_sample.php
    
以下のコードを記述してみましょう。

```php
<?php

$num = 5;

//$numが3より大きい、かつ7より小さいという条件
if($num > 3 && $num < 7) {    
    echo '3より大きいかつ7より小さいです';
else {
    echo '条件に当てはまりません';
}


?>
```

実行結果

    3より大きいかつより小さいです

`&&`を用いた場合、`$$`の左右にある条件をどちらとも満たす場合のみ`true`を返します。

ですので、以下の場合は`false`を返します。

```php
<?php

$num = 5;

//$numが3より大きい、かつ5より小さいという条件
if($num > 3 && $num < 5) {    
    echo '3より大きいかつ5より小さいです';
else {
    echo '条件に当てはまりません';
}


?>
```

実行結果

    条件に当てはまりません

5より小さいというのは5は含まれないので上記のような実行結果になります。

まとめると`A && B`の返り値は以下の通りとなります。

|Aの結果|Bの結果|A && Bの結果|
|---|---|---|
|true|true|true|
|true|false|false|
|false|true|false|
|false|false|false|



### AまたはB

条件分岐の条件で`AまたはB`を設定するためには`||`を使います。

それでは、以下の名前のファイル名を作成しましょう。（index.phpを上書きしても構いません）

    or_sample.php
    
以下のコードを記述してみましょう。

```php
<?php
    
$num = 10;

//$numが3以下、または7以上という条件
if($num <= 3 || $num >= 7) {    
    echo '3以下または5以上です';
else {
    echo '条件に当てはまりません';
}

?>
```

実行結果

    3以下または5以上です

`||`を使った条件では少なくともどちらかの条件が`true`であれば`true`を返します。

どちらも`false`の時にだけ`false`を返します。

まとめると`A || B`の返り値は以下の通りとなります。

|Aの結果|Bの結果|A || Bの結果|
|---|---|---|
|true|true|true|
|true|false|true|
|false|true|true|
|false|false|false|

### 条件分岐課題

以下の条件を満たすプログラムを記述してください。

- 任意を変数を定義し、値として5を格納する
- その変数の値が3より小さい時に「3より小さいです」と出力する
- その変数の値が3以上かつ8より小さい時に「3以上かつ8より小さいです」と出力する
- それ以外の場合は「8以上です」と出力する

### まとめ
条件分岐に関して`if`、`switch`、`かつ、または`を学習してきました。条件分岐はプログラミングをする上でかなり重要な考え方です。実務でも当たり前のように使用しますので、焦らずしっかりと理解していってください。

条件分岐は以上です。

お疲れ様でした！

