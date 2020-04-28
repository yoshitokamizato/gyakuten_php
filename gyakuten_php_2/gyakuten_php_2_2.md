### switch

`PHP`の条件分岐には`if`の他に`switch`があります。

`switch`は条件がたくさんあり、かつ、「〜と〜が等しい」みたいな条件を判定する場合に使うことがあります。

|文法|特徴|
|---|---|
|if|~以上、~以下と行った判定ができる|
|switch|1つの比較対象に対して複数の条件分岐を行う|

`switch`が適しているケースにおいても`if`を使って書くことはできますが、条件が多い場合に`elseif{ }`をたくさん書くことになりコード量も多くなるので`if`と`switch`はケースによって使い分けると良いです。

以下が、`switc`の使用例です。

それでは、以下の名前のファイル名を作成しましょう。（index.phpを上書きしても構いません）

    switch_sample.php

```php
<?php

$fruits = "apple";

//比較対象をcaseの後に記述
switch($fruits) {
//比較対象と比較する値を記述
    case "banana":
		echo "バナナです";
        break;
    case "apple":
		echo "りんごです";
        break;
    case "orange":
		echo "オレンジです";
        break;
    case "mango":
		echo "マンゴーです";
        break;
    default:
		echo "不正な名前です";
}

?>
```
実行結果

    りんごです

ちなみに、この`switch`では複数の条件（変数の範囲）による条件分岐は以下のように記述します。

`break`はその時点で`switch`内の処理を終了させるための物です。

`default`はどの`case`にも当てはまらなかった場合の処理を記述します。`if`文でいう`else`と同じ使い方です。

```php
<?php
    
$month = 6;

//比較対象をcaseの後に記述
switch($month) {
//比較対象と比較する値を記述
    case 3:
    case 4:
    case 5:
		echo "春です";
        break;
    case 6:
    case 7:
    case 8:
		echo "夏です";
        break;
    case 9:
    case 10:
    case 11:
		echo "春です";
        break;
    case 12:
    case 1:
    case 2:
		echo "春です";
        break;
    default:
        echo "不正な値です";
        
?>
```
実行結果

	夏です
    
ただ、`switch`で複数の条件（変数の範囲など）の条件分岐をする場合、上記のようにコードがかなり長くなってしまうため、`if`を使う方がコード量もスッキリします。

### まとめ
`switch`が使えるようになると、行える処理もかなり柔軟になります。現場でも使用することはありますので、`switch`を使って無駄なく柔軟にプログラムを書く練習をなんどもやってみてください。

お疲れ様でした！