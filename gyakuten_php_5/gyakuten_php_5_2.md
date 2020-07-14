## 戻り値
関数の基本的な使い方、そして関数を自作する方法を学んできました。

今回は「戻り値」についてみていきましょう。

戻り値を理解することで関数をもっと便利に使えるようになります。

関数は`引数`と呼ばれる値を渡すことができ、定義された`処理`を行うものでしたね。

`処理を行って返された結果`これが「戻り値」です。また、返り値とも呼ばれます。

「引数」を渡し「戻り値」が返ってくるわけです。

まずは前回の講座で定義したprintName関数をみてみましょう。

```php
<?php
// 関数の定義    
function printName($name) {
    echo "私の名前は" . $name . "です。";
}
// 関数の呼び出し
printName('佐藤');

?>
```

この関数は波かっこ`{}`の中の処理の部分で`echo`を使い出力しています。

ですので引数を渡し関数を呼び出せば

```
私の名前は佐藤です。
```

と表示されます。

このように出力を伴う関数では戻り値の指定は特にしていませんでしたが、出力を伴うものでない関数を作ることもできます。

その場合に戻り値を指定することができるのです。

では戻り値を指定する方法をみていきましょう。

```
function 関数名(引数){
  処理内容;
  return 戻り値;
};

```
このように記述します。

`return`の後に返したい値を記述するだけです。戻り値にはどんな値を指定してもOKです。

文字列、数値だけでなく配列など全ての値を指定することができます。

では実際に使用していきましょう。


```php

<?php
// 関係の定義
function calc($num1, $num2) {
    $total = $num1 + $num2;
    return $total;
}

?>

```

calcという名前の関数を定義しました。

引数に$num1と$num2という値を渡し、それらを足した結果を$total変数に代入し戻り値として指定しています。

例えばこのcalc関数を以下のように`return`で戻り値を指定せず、printName関数と同様に`echo`を使い出力を伴う処理とした場合

```php

<?php
// 関係の定義
function calc($num1, $num2) {
    echo $num1 . "と" . $num2 . "を足した値は" . $num1 + $num2 . "です。";
}
// 関数の呼び出し
calc(4, 8);

?>

```

実行結果

```
4と8を足した値は12です。
```

となります。

しかし先の`return`を使用して定義したように、この関数では「二つの値を足す」までとしておき、その結果を戻り値として指定することで次のような使い方ができます。

```php

<?php
// 関係の定義
function calc($num1, $num2) {
    $total = $num1 + $num2;
    return $total;
}

$total_A = calc(4, 8);
$total_B = calc(2, 5);

echo "Aの合計は" . $total_A . "です。";
echo "Bの合計は" . $total_B . "です。";

echo "AとBの差は" . $total_A - $total_B . "です。";

?>

```

実行結果
```
Aの合計は12です。
Bの合計は7です。
AとBの差は5です。
```

AとBそれぞれの合計を求め、さらにその差を求めました。

このように、求めた値を使ってまた別の計算をしたり、変数に保持しておきまた別の場所で使うなどのふるまいをすることができるのです。

また、`return`には**「関数内の処理をそこで終了する」**という機能もあるので注意が必要です。

例えばこのように書いた場合

```php

<?php
// 関係の定義
function calc($num1, $num2) {
    $total = $num1 + $num2;
    return $total;
    
    echo $num1 . "と" . $num2 . "を足した値は" . $num1 + $num2 . "です。";
}
// 関数の呼び出し
$result = calc(4, 8);
echo "合計は" . $result . "です。";
?>

```

実行結果

```
合計は12です。
```

となり、calc関数のブロック内に記述した`echo`の内容が出力されることはありません。

他にも、条件件分岐と組み合わせて関数内に`return`を複数使うこともできます。

calc関数の処理内容を変更しています。みてみましょう。

```php

<?php
// 関係の定義
function calc($num1, $num2) {
    $total = $num1 + $num2;
    
    if ($total > 9) {
      return "合格"; 
    }

    return "不合格";
}

// 関数の呼び出し
$result_A = calc(4, 8);
$result_B = calc(3, 2);

echo "Aの結果：" . $result_A;
echo "Bの結果：" . $result_B;


?>

```

実行結果

```
Aの結果：合格
Bの結果：不合格
```

となります。

合計が9を超えていたら「合格」をそれ以外は「不合格」を戻り値に指定しています。

### まとめ
戻り値を変数に代入し、好きなかたちで出力する。また別の処理をする。

少し複雑でしたが、このような戻り値の使い方を理解することで関数をより便利に使うことができます。

組み込み関数にも戻り値をもつものが圧倒的に多いです。

関数の基本は、`「引数」を渡し、「戻り値」が返ってくる`です。

何度も繰り返し復習してしっかりと理解していきましょう。

今回は以上です。

お疲れ様でした！