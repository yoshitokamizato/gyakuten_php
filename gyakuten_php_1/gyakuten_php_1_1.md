## PHPの基本

### PHPとはどんな言語か
`PHP`とは動的にWebページを生成することができる`サーバーサイド`のスクリプト言語です。他のプログラミング言語と比較して仕様や文法が比較的わかりやすく、初学者でも習得しやすいと言われています。

また`MySQL`などのデータベースとの連携が容易なことなどから、`WordPress`（この講座では扱いません）を含めたWebアプリケーションの開発にもよく使われる有名なスクリプト言語でもあります。

`PHP`と同じサーバーサイドのスクリプト言語には`Ruby`、`Python`、`Java`などがあります。

### 言語バージョン
本教材は以下の条件で動作確認しております。

    PHP：version 7.3.11
    ブラウザ：Google Chrome

プログラミングでWebアプリケーションを開発していく上でよっぽどの理由がない限りはブラウザは`Google Chrome`を使いますので、`Google Chrome`をダウンロードしていない方はダウンロードしておいてください。

### 基本の書き方

PHPを使用した処理は以下のように書きます。

```php
<?php

//処理したい内容

?>
```

`<?php`と`?>`の間に処理したい内容を書いていきます。

`<? php>`のように?とphpの間に**半角スペース**を入れてしまうとエラーとなり処理が実行されないのでご注意ください。

### 「?>」の省略について
コードの結びの`?>`ですが、その後に`HTML`や`JavaScript`などの他の言語のコードがない時は以下のように文末の`?>`を省略することもできます。

（超余談ですが、PHPのフレームワークの中には`?>`を省略しなければならないものあります）

```php
<?php

//処理したい内容
```

ですが、ポピュラーな書き方としては結びに`?>`をつける方ですので、本講座のテキストではコードの終わりに`?>`を付けて進めてきます。

今は「へえ、なるほど」くらいで良いですが、`HTML`のタグの中に`PHP`のコードを書くこともあり、その場合は以下のように`<?php`と`?>`が必須となります。

```html

//HTMLのタグの中にPHPのコードを埋め込む時
<P><?php echo 'Hello World!'; ?></p>

```

また、初心者向けのPHPの書籍、とても有名なプログラミング教材である`Progate`などでも

```php
<?php

//処理したい内容

?>
```

のように終わりに`?>`をつけた書き方で紹介されていますので問題ないと思います。

これから少しずつ、`PHP`でのプログラムの書き方について勉強していきます。頑張りましょう！
