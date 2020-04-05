## PHPの基本

### 言語バージョン
本教材は以下の条件で動作確認しております。

    PHP：version 7.3.11
    ブラウザ：Google Chrome

### 基本の書き方

PHPを使用した処理は以下のように書きます。

```php
<?php

//処理したい内容

?>
```
`<?php`と`?>`の間に処理したい内容を書いていきます。

`<? php>`のように?とphpの間に**半角スペース**を入れてしまうとエラーとなり処理が行われないのでご注意ください。

### 「?>」の省略について
PHPのコードでは以下のように文末の`?>`を省略することもできます。

（PHPのフレームワークの中には`?>`を省略しなければならないものあります）

```php
<?php

//処理したい内容
```

ですが、HTMLの中にPHPの処理を埋め込む時には`?>`が**必須**になりますので、このサロンのテキストではコードの終わりに`?>`を付けて進めてきます。

ちなみに初心者向けのPHPの書籍、Progate等でも

```php
<?php

//処理したい内容

?>
```
のように終わりに`?>`をつけた書き方で紹介されています。