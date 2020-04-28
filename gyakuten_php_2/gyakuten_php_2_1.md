## 条件分岐
条件分岐とは、「もし〜だったら〜の処理をする」というように、条件によって行う処理を変えるために使用されるものです。条件分岐を実装するときには`if`や`switch`を使用します。ではさっそく、それぞれの使い方を学んでいきましょう。

### if
ifの基本的な書き方は以下の通りとなります。

```php
<?php
    
$hp = 10;

if($hp >= 10) {
  echo "勇者のHPは10以上だ";
}

?>
```

`if`の右側に書かれている`($hp >= 10)`が条件式となります。こちらの評価結果が成り立つ場合に、`{`と`}`で囲まれた部分の処理が実行されます。条件式にかかれている`>`=の部分は比較演算子と呼ばれ、以下のような種類があることを理解しておきましょう。

|比較演算子|意味|
|---|---|
|a >= b|aはb以上|
|a <= b|aはb以下|
|a > b|aはbより大きい|
|a < b|aはbより小さい|
|a == b|aはbと等しい|
比較演算子の中でも`a == b`の部分を`a = b`という風に`=`を1つ書き忘れることがよくあるので気をつけてください。それだと「代入」という意味になってしまいます。また、比較演算子は実行されると`true（はい）`か`false（いいえ）`が結果として返ってくることを理解しておきましょう。

それでは、以下の名前のファイル名を作成しましょう。（index.phpを上書きしても構いません）

    if_sample.php

if_sample.phpが作成できたら、次のコードを書いてください。

```php
<?

$a = 10;
$b = 15;

echo "aはb以上？：";
var_dump($a >= $b);
echo "<br>";
echo"aはb以下？：";
var_dump($a <= $b);
echo "<br>";
echo "aはbより大きい？：";
var_dump($a > $b);
echo "<br>";
echo "aはbより小さい？：";
var_dump($a < $b);
echo "<br>";
echo "aはbと同じ？：";
var_dump($a == $b);
echo "<br>";
?>
```

コードが記述できたら、`MAMP`を起動させて、ブラウザに表示させてください。

UPLは`http://localhost:8888/htdocs配下のディレクトリ名`

実行結果

    aはb以上？：bool(false)
    aはb以下？：bool(true)
    aはbより大きい？：bool(false)
    aはbより小さい？：bool(true)
    aはbと同じ？：bool(false)

先ほどのコード中の以下のコードについて軽く解説します。

    var_dump($a >= $b);
    echo "<br>";
    
まず、`var_dump`ですが、こちらも`echo`と同様に出力するための命令です。`echo`と異なるところは出力するもののデータの型を出力してくれるところです。

実行結果の

    bool(false)
    
というのは`Boolean型（trueかfalse）`というデータ型で`false`という値を出力していることになります。

試しに`var_dump('Hello Word!');`や`var_dump(2020);`などをブラウザで表示させてみて`echo`との違いを確認してみてください。

次に`echo "<br>";`ですが、これは改行です。

では先ほどのコードの解説の続きですが、`if`は比較演算子の評価結果が`true`になるか`false`になるかを判断し、行う処理を決めています。

そのため、以下のように記述してもエラーは表示されず、きちんと処理が実行されます。

```php
<?php

//条件がtrueの場合は実行される
if(true){
    echo "実行されます";
}

//条件がfalseの場合は実行されない
if(false){
  echo "実行されません";
}

?>

```

実行結果

    実行されます
    
このように、`if`の条件式に使用されている比較演算子では、評価結果として`true`か`false`かの判定が行われていることを理解しておいてください。

### else
`if`の部分に書いた条件式の評価結果が`false`のときに行いたい処理がある場合は`else`を使用します。

```php
<?php
    
$hp = 5;

if($hp >= 10){
  echo "勇者のHPは10以上だ";
}else{
  //ifの条件が成り立たない場合の処理
  echo "勇者のHPは10より下だ";
}

?>
```
`else`を使用することによって、わざわざもう１つ`if`文を書かなくてもよくなり、コードがスマートになります。

以下が、ちょっとイマイチな例です。

```php
<?php
    
$hp = 5;

if($hp >= 10){
  echo "勇者のHPは10以上だ";
}

if($hp < 10){
  echo "勇者のHPは10より下だ";
}

?>
```
`if`をわざわざ２つ書いているので、表現が冗長ですね。このような場合は、`else`を使った方がスッキリします。

### elseif
`elseif`は`if`の部分に加え、さらに条件を追加したいときに使用します。

`Ruby`では`elsif`と書きますが、`elseif`だということに注意してくださいね！

```php
<?php
    
$hp = 3;

if($hp > 10){
  echo "勇者は元気だ";
//複数の条件を指定するときに使う
}elseif($hp > 5){
  echo "勇者は弱っている";
}elseif($hp > 3){
  echo "勇者はかなり弱っている";
}elseif($hp > 0){
  echo "勇者は瀕死だ";
}else{
  echo "勇者はしんだ";
}

?>
```
この`elseif`も、複数条件で処理を行いたいときに、冗長な表現を避けることができます。

ちなみに、`elseif`を使わないとこんな感じになります。

```php
<?php
    
$hp = 3;

if($hp > 10){
  echo "勇者はピンピンしている";
}

if($hp > 10){
  echo "勇者は元気だ";
}

if($hp > 5){
  echo "勇者は弱っている";
}

if($hp > 3){
  echo "勇者はかなり弱っている";
}

if($hp > 0){
  echo "勇者は瀕死だ";
}

if($hp <= 0){
  echo "勇者はしんだ";
}

?>
```
うん、超めんどくさい！笑

冗長なコードを避けるためにも`elseif`と`else`を使えるように心掛けましょう。

ちなみに、条件がたくさんあり、かつ、「〜と〜が等しい」みたいな条件を判定する場合は、`switch`を使うこともあります。`switch`は後ほどの講座で解説します。

### ifの省略形
実は、`if`は1行で書くこともできます。条件を１つしか判定しない場合はこのほうがスッキリするので、意識して使うようにして見てください。実際に現場でもこの使い方はよく見ます。

```php
<?php
    
//省略形
if($hp >= 10) echo "勇者のHPは10以上だ";
if($hp >= 10) ? echo "勇者のHPは10以上だ";

?>
```

### 三項演算子
見慣れていない方はちょっと混乱されるかもしれませんが、条件分岐には`三項演算子`というものも存在します。ちょっと書き方は複雑ですが、こちらも現場ではよく用いられるものなので、使えるように意識してみてください。
```php
<?php
    
$hp = 11;

//条件式(true or false) ? trueの時に行いたい処理 : falseの時に行いたい処理
echo ($hp > 10) ? "勇者のHPは10より大きいです" : "勇者のHPは10より小さいです";

?>
```

### サンプルプログラム
それでは、`if`を利用したサンプルプログラムを作っていきましょう！

まずは、以下のような名前のファイルを作成し、保存します。（index.phpを上書きしても構いません）

    conditional.php

それでは、`conditional.php`にコードを書いていきましょう。今回は、`if`を使用して戦闘ゲームを再現していきます。

まずは、それぞれのキャラクターのパラメータを変数に入れましょう！慣れない人は、`//`でコメントも書いておくと、後から見返したときに理解しやすいです。

```php
<?php

//勇者のhp
$brave_hp = 30;
//勇者の攻撃力
$brave_attack = 10;
//勇者の防御力
$brave_defense = 5;
//敵のhp
$enemy_hp = 30;
//敵の攻撃力
$enemy_attack = 5;
//敵の防御力
$enemy_defense = 10;

?>
```

それでは次に、キャラクターが攻撃をするときの処理を書いていきましょう。

```php
<?php
    
$brave_hp = 30;
$brave_attack = 10;
$brave_defense = 5;

$enemy_hp = 30;
$enemy_attack = 5;
$enemy_defense = 10;

//敵に与えるダメージの計算
$enemy_damage = $brave_attack - $enemy_defense;

?>
```

敵に与えるダメージの計算ができたら、それを敵のHPから引き算してダメージを与える処理を書きます。

```php
<?php
    
$brave_hp = 30;
$brave_attack = 10;
$brave_defense = 5;

$enemy_hp = 30;
$enemy_attack = 5;
$enemy_defense = 10;

$enemy_damage = $brave_attack - $enemy_defense;
//敵のHPにダメージを与える
$enemy_hp = $enemy_hp - $enemy_damage;

?>
```

敵にダメージを与えるコードが追加できたら、`if`を利用して、残りHPによって敵キャラのリアクションを変えるようにしましょう！

```php
<?php
$brave_hp = 30;
$brave_attack = 10;
$brave_defense = 5;

$enemy_hp = 30;
$enemy_attack = 5;
$enemy_defense = 10;

$enemy_damage = $brave_attack - $enemy_defense;
$enemy_hp = $enemy_hp - $enemy_damage;

//敵に与えるダメージと残りHPの表示
echo "敵に".$enemy_damage."のダメージを与えた。";
echo "<br>";
echo "残りHPは".$enemy_hp."だ。";
echo "<br>";

//残りHPによってリアクションを変える
if($enemy_hp > 20){
  echo "敵は元気だ";
}elseif($enemy_hp > 10){
  echo "敵はちょっと弱っている";
}elseif($enemy_hp > 5){
  echo "敵はかなり弱っている";
}elseif($enemy_hp > 0){
  echo "敵は瀕死だ";
}else{
  echo "敵はしんだ";
}

?>
```

それでは同様に、敵から勇者へ攻撃を行うときの処理も追加していきましょう！できるひとは、サンプルコードを見ずに自分で考えてコードを書いて見てください。自分で考えてコードを書くと、かなり勉強になりますよ。

```php
<?php
    
$brave_hp = 30;
$brave_attack = 10;
$brave_defense = 5;

$enemy_hp = 30;
$enemy_attack = 5;
$enemy_defense = 10;

$enemy_damage = $brave_attack - $enemy_defense;
$enemy_hp = $enemy_hp - $enemy_damage;

echo "敵に".$enemy_damage."のダメージを与えた。";
echo "<br>";
echo "残りHPは".$enemy_hp."だ。";
echo "<br>";

if($enemy_hp > 20){
  echo "敵は元気だ";
}elseif($enemy_hp > 10){
  echo "敵はちょっと弱っている";
}elseif($enemy_hp > 5){
  echo "敵はかなり弱っている";
}elseif($enemy_hp > 0){
  echo "敵は瀕死だ";
}else{
  echo "敵はしんだ";
}

echo "<br>";

//敵に与えるダメージの計算
$brave_damage = $enemy_attack - $brave_defense;
//敵のHPにダメージを与える
$brave_hp = $brave_hp - $brave_damage;

//敵に与えるダメージと残りHPの表示
echo "敵から".$brave_damage."のダメージを受けた。";
echo "<br>";
echo "残りHPは".$brave_hp."だ。";
echo "<br>";

//残りHPによってリアクションを変える
if($brave_hp > 20){
  echo "勇者は元気だ";
}elseif($brave_hp > 10){
  echo "勇者はちょっと弱っている";
}elseif($brave_hp > 5){
  echo "勇者はかなり弱っている";
}elseif($brave_hp > 0){
  echo "勇者は瀕死だ";
}else{
  echo "勇者は死んだ";
}

?>
```

コードを書いたら、プログラムを実行して動作確認してみましょう。
エラーが表示されていなければ完成です。

以上で簡単なゲームの再現はできました。
しかし、こちらのコードにはまだまだ改善の余地があります。

では、これからサンプルコードを改善（リファクタリング）していきましょう。

現在の内容だと攻撃の処理において決まった値しか計算されないことです。

これではゲーム性がないので、次に、与えるダメージがある一定の範囲で変化するような処理を書いて見ましょう。

この処理を実装するときには`mt_rand`というメソッドを使います。

この`mt_rand`は、数字を指定するとその中からランダムな値を表示してくれます。これを利用して、攻撃の処理をするさいのダメージを変化するように実装して見ましょう。

その際、`3,5`といった`範囲オブジェクト（Range）`というものを使用して`mt_rand`を記述すると、指定した範囲の中でランダムな値（乱数）を表示してくれるようになります。

ちなみに乱数を生成するメソッドには`rand`がありますが、`mt_rand`の方が高速な処理が可能なので`mt_rand`を使うようにしてください。

```php
<?php
    
$brave_hp = 30;
$brave_attack = 10;
$brave_defense = 5;

$enemy_hp = 30;
$enemy_attack = 5;
$enemy_defense = 10;

//攻撃にランダム要素を入れる
//範囲オブジェクト　3,5
$enemy_damage = $brave_attack - $enemy_defense + mt_rand(3,5);
$enemy_hp = $enemy_hp - $enemy_damage;

echo "敵に".$enemy_damage."のダメージを与えた。";
echo "<br>";
echo "残りHPは".$enemy_hp."だ。";
echo "<br>";

if($enemy_hp > 20){
  echo "敵は元気だ";
}elseif($enemy_hp > 10){
  echo "敵はちょっと弱っている";
}elseif($enemy_hp > 5){
  echo "敵はかなり弱っている";
}elseif($enemy_hp > 0){
  echo "敵は瀕死だ";
}else{
  echo "敵はしんだ";
}

echo "<br>";

//攻撃にランダム要素を入れる
//範囲オブジェクト　3,5
$brave_damage = $enemy_attack - $brave_defense + mt_rand(3,5);
$brave_hp = $brave_hp - $brave_damage;

echo "敵から".$brave_damage."のダメージを受けた。";
echo "<br>";
echo "残りHPは".$brave_hp."だ。";
echo "<br>";

if($brave_hp > 20){
  echo "勇者は元気だ";
}elseif($brave_hp > 10){
  echo "勇者はちょっと弱っている";
}elseif($brave_hp > 5){
  echo "勇者はかなり弱っている";
}elseif($brave_hp > 0){
  echo "勇者は瀕死だ";
}else{
  echo "勇者は死んだ";
}

?>
```

また、`mt_rand`を使用すれば通常攻撃とクリティカルヒットをランダムに発生させることもできます。

```php
<?php

$brave_hp = 30;
$brave_attack = 10;
$brave_defense = 5;

$enemy_hp = 30;
$enemy_attack = 5;
$enemy_defense = 10;

//攻撃にランダム要素を入れる
//mt_rand(0,3)にすると0~3のうちランダムに数字を発生させる
$select_attack = mt_rand(0,3);

if($select_attack == 0){
  echo "かいしんのいちげき";
  //mt_randの範囲を20~30と大きな値にする
  $enemy_damage = $brave_attack - $enemy_defense + mt_rand(20,30);
  $enemy_hp = $enemy_hp - $enemy_damage;
}else{
  echo "つうじょうこうげき";
  $enemy_damage = $brave_attack - $enemy_defense + mt_rand(3,5);
  $enemy_hp = $enemy_hp - $enemy_damage;
}

echo "<br>";

echo "敵に".$enemy_damage."のダメージを与えた。";
echo "<br>";
echo "残りHPは".$enemy_hp."だ。";
echo "<br>";

if($enemy_hp > 20){
  echo "敵は元気だ";
}elseif($enemy_hp > 10){
  echo "敵はちょっと弱っている";
}elseif($enemy_hp > 5){
  echo "敵はかなり弱っている";
}elseif($enemy_hp > 0){
  echo "敵は瀕死だ";
}else{
  echo "敵はしんだ";
}

echo "<br>";

//攻撃にランダム要素を入れる
//mt_rand(0,3)にすると0~3のうちランダムに数字を発生させる
$select_attack = mt_rand(0,3);

if($select_attack == 0){
  echo "かいしんのいちげき";
  //mt_randの範囲を10~20と大きな値にする
  $brave_damage = $enemy_attack - $brave_defense + mt_rand(10,20);
  $brave_hp = $brave_hp - $brave_damage;
}else{
  echo "つうじょうこうげき";
  $brave_damage = $enemy_attack - $brave_defense + mt_rand(3,5);
  $brave_hp = $brave_hp - $brave_damage;
}
    
echo "<br>";

echo "敵から".$brave_damage."のダメージを受けた。";
echo "<br>";
echo "残りHPは".$brave_hp."だ。";
echo "<br>";

if($brave_hp > 20){
  echo "勇者は元気だ";
}elseif($brave_hp > 10){
  echo "勇者はちょっと弱っている";
}elseif($brave_hp > 5){
  echo "勇者はかなり弱っている";
}elseif($brave_hp > 0){
  echo "勇者は瀕死だ";
}else{
  echo "勇者は死んだ";
}

?>
```
これでだいぶリファクタリングができました。他にも自分なりに工夫できる部分はあるかと思いますので、ぜひこちらのコードをカスタマイズしてオリジナルプログラムを組んでみてください。

### 条件分岐課題
旅行プログラムを作成してください。

条件

条件分岐を使用してください

仕様

・旅行プランの選択を要求（getsを使用）
・人数の入力を要求（getsを使用）
・5人以上なら10%割引

実行例
```
旅行プランを選択してください
1. 沖縄旅行（¥10,000）
2. 北海道旅行（¥20,000）
3. 九州旅行（¥15,000）

プランを選択 > 1

沖縄旅行ですね、何人で行きますか？

人数を入力 > 10

5人以上なので10%割引となります

合計料金：¥45,000
```

### まとめ
`if`が使えるようになると、行える処理もかなり柔軟になります。現場でもよく使用するので、`if`を使って無駄なく柔軟にプログラムを書く練習をなんどもやってみてください。

`mt_rand`メソッドも使用頻度が多いメソッドですのでぜひ覚えておいてください。

お疲れ様でした！