###  配列と繰り返し処理
配列は、繰り返し処理と組み合わせると処理の効率が格段に上がります。その際、配列との組み合わせでよく利用されるのが、繰り返し処理の部分で学んだeachです

users = ["satou", "tanaka", "yamada", "shimizu"]

users.each do |name|
  puts "Hello!! #{name}."
end
実際に現場では、1万件以上のユーザーのデータをデータベースから取り出して表示することもあるので、配列と繰り返し処理を組み合わせて使用しないと大変なことになります。「配列から要素を取り出すときは繰り返し処理で取り出す」ということを頭に入れておきましょう。ages[0]のような取り出し方は、現場ではほとんど使用しません。

配列課題
Ruby、PHP、Javaそれぞれの言語で「Hello World」をコンソール（ターミナル、コマンドプロンプトなど）に出力するためのコードを提示するプログラムを作成してください。

条件
条件分岐と配列を使用してください

実行結果

様々な言語のHello World

Ruby：puts "Hello World!"
PHP：echo "Hello World!";
Java：System.out.println("Hello World!");



eachは配列や範囲オブジェクトに対して使用することができる繰り返し処理です。ちなみに、配列とは何個も要素を格納することができるもので、範囲オブジェクトとは0~100のように、数値的な範囲を表すデータのことです。

それではさっそく、eachの使い方を確認していきましょう。以下のようにコードを記述してください。

# 配列 複数のデータを格納できる
users = ["satou", "tanaka", "yamada", "shimizu"]

# 配列に対してeach文で中身を表示
# usersの要素１つ１つをnameに代入してブロック内の処理を実行
users.each do |user|
  puts "Hello!! #{user}."
end
実行結果

Hello!! satou
Hello!! tanaka
Hello!! yamada
Hello!! shimizu
はじめてeachを見る人なら混乱するかと思います。落ち着いて、1つ1つ確認しながら進めていきましょう。まず、eachのこの部分から。

users.each do |user|
  # 行いたい処理
end
上の中でusersは複数の要素が入った配列になります。その配列に対してeachを実行することによって、要素を1つ1つ取り出して処理を行うことができるわけです。で、そのときに大切になってくるのが配列から取り出された各要素が||の中に囲まれたuserに代入されることです。

まとめると、配列のusersに対してeachを使用すると、1つ1つの要素がuserに代入され、doとendで囲まれた部分の処理が実行されるということになります。

このeachについては、構文がわりと複雑なので理解がしにくいかと思いますが、いろんなサンプルを書いて実行し、eachを書くことに慣れていきましょう。

ages = [20, 60, 27, 23]

ages.each do |age|
  puts "I'm #{age} years old."
end
items = ["book", "food", "movie", "music"]

items.each do |item|
  puts "I bought #{item}"
end
prefectures = ["Hokkaido", "Okinawa", "Saitama", "Ibaraki"]

prefectures.each do |prefecture|
  puts "#{prefecture} is awesome!!"
end
each.with_index
eachと似た繰り返し処理として、each.with_indexがあります。これは、名前の通り繰り返し処理であるeachをindex番号付きで実行するということになります。基本的な書き方は以下の通り。

users = ["satou", "tanaka", "yamada", "shimizu"]

# インデックス番号と配列の要素を同時に出力
users.each.with_index do |name, i|
  puts "No.#{i} #{name}"
end
実行結果

No.0 satou
No.1 tanaka
No.2 yamada
No.3 shimizu
実行結果のように、each.with_indexを利用すると、番号付きで繰り返し処理を実行してくれます。今回のサンプルのように会員No.を表示したいときなどに非常に便利です。

では、コードの解説に移りましょう。

each.with_indexでは、配列の中身が||で囲んだ部分に代入されるのは、前項で学んだeachと同じです。異なる部分は、||の中の変数が２つになることです。この2番目の変数の中に、インデックス番号の情報が格納されます。

# 変数iにインデックス番号の情報が入る（iでなくてもindexやnumなどでも良い）
users.each.with_index do |name, i|
  # iを利用してカウント
  puts "No.#{i} #{name}"
end
ただ、実行結果をよく見ると一番最初の番号が0になっていますね。

No.0 satou
No.1 tanaka
No.2 yamada
No.3 shimizu
これはちょっと不自然なので、No.1からカウントを開始できるようにしてみましょう。

実はeach.with_indexは、インデックスの開始番号を指定できるようになっています。

users = ["satou", "tanaka", "yamada", "shimizu"]

# インデックスの開始番号を指定
users.each.with_index(1) do |name, i|
  puts "No.#{i} #{name}"
end
実行結果

No.1 satou
No.2 tanaka
No.3 yamada
No.4 shimizu
each.with_indexはeachと合わせて非常によく使われるので、ぜひ練習してみてください。

ages = [20, 60, 27, 23]

ages.each.with_index(1) do |age, i|
  puts "No.#{i} I'm #{age} years old."
end
items = ["book", "food", "movie", "music"]

items.each.with_index(1) do |item, i|
  puts "No.#{i} I bought #{item}"
end
prefectures = ["Hokkaido", "Okinawa", "Saitama", "Ibaraki"]

prefectures.each.with_index(1) do |prefecture, i|
  puts "No.#{i} #{prefecture} is awesome!!"
end
サンプルプログラム
では、これから繰り返し処理を使用してサンプルプログラムを作っていきましょう

今回は、「任意のメンバーを2つのチームに分ける」というプログラムをサンプルにコードを書いていきます。

まずはじめに、名前を格納するための配列を作成しましょう。

# チーム分けするメンバーの名前を格納する配列を定義
user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]
配列が作成できたら、その配列から要素を取り出すためのeachを書いていきます。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

# 配列を取り出すためのeach
user_list.each.with_index do |user, i|

end
eachを書いたら、その中に各メンバーをチーム分けするための処理を書いていきます。

その際、odd?というメソッドを使用します。このodd?は整数オブジェクト（Integer）で使用できるメソッドで、整数が奇数だったらtrueを返し、そうじゃなかった場合はfalseを返します。そのため、ifなどの条件分岐を併せて利用されることが多いです。

ちなみに、odd?の他にはeven?もあります。even?は、整数オブジェクトが偶数ならtrueを返し、そうじゃなかった場合はfalseを返します。

メソッド	処理
odd?	奇数ならtrue、偶数ならfalse
even?	偶数ならtrue、奇数ならfalse
それでは、odd?を使用してチーム分けの処理を書いてみましょう。その際、チーム分けしたメンバーを格納するための配列を用意します。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

# チームA,Bのメンバーを格納するための配列
team_a = []
team_b = []

user_list.each.with_index do |user, i|
  if i.odd?
    # 配列に要素を格納する
    team_a << user
  else
    # 配列に要素を格納する
    team_b << user
  end
end
各チームの配列にメンバーを格納する処理ができたら、次はそのメンバーを表示するための処理を書きましょう。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

team_a = []
team_b = []

user_list.each.with_index do |user, i|
  if i.odd?
    team_a << user
  else
    team_b << user
  end
end

# チームAのメンバーを表示
puts "チームA"
puts team_a
puts ""
# チームBのメンバーを表示
puts "チームB"
puts team_b
これで一通り、チーム分けのプログラムは完了しました。

しかし、まだまだ改善の余地はあります。ここからどんどんリファクタリングしていきましょう。

まずは、チームメンバーの情報を変数に格納して一気に表示できるようにします。その際、+=を使用することで、変数の中に格納された文字列に対して、追加で文字列を足し合わせていきます。このような処理を文字列連結といいます。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

team_a = []
team_b = []

user_list.each.with_index do |user, i|
  if i.odd?
    team_a << user
  else
    team_b << user
  end
end

# チームAのメンバーを表示
text = "チームA"
team_a.each do |member|
  # テキストに文字列連結
  text += member
end
# チームBのメンバーを表示
text += "チームB"
team_b.each do |member|
  # テキストに文字列連結
  text += member
end

# チーム分けの情報を表示
puts text
これでputsを使用する回数を減らすことができたのですが、実行してみると表示がおかしなことになってしまいます。

実行結果

チームASaitouImaiTakahashiチームBYanagiAoyagiObata
これではかえって読みにくくなってしまうので、途中に改行を入れるようにしてみましょう。

Rubyの文字列の中で改行を行いたい場合は、改行コード\nを使用します。nの前にある\（バックスラッシュ）を入力したい場合はoption + ¥を押しましょう。そうすると、\を入力することができます。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

team_a = []
team_b = []

user_list.each.with_index do |user, i|
  if i.odd?
    team_a << user
  else
    team_b << user
  end
end

# \nを入れて改行
text = "チームA\n"
team_a.each do |member|
  text += "#{member}\n"
end
text += "\nチームB\n"
team_b.each do |member|
  text += "#{member}\n"
end

puts text
これで、読みやすく表示することができるようになりました。

実行結果

チームA
Saitou
Imai
Takahashi


チームB
Yanagi
Aoyagi
Obata
ただ、各メンバーを表示するだけなら、あまりeachを使用するメリットはありません。以下のように記述しても、スッキリと書くことができるからです。

puts "チームA"
puts team_a
puts ""
puts "チームB"
puts team_b
ただ、各チームメンバーに対して文字列を付け加えたい場合は、eachの方が便利です。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

team_a = []
team_b = []

user_list.each.with_index do |user, i|
  if i.odd?
    team_a << user
  else
    team_b << user
  end
end

text = "チームA\n"
team_a.each do |member|
  # チームメンバーを「〜さん」と表示する
  text += "#{member}さん\n"
end
text += "\nチームB\n"
team_b.each do |member|
  # チームメンバーを「〜さん」と表示する
  text += "#{member}さん\n"
end

puts text
実行結果

チームA
Saitouさん
Imaiさん
Takahashiさん

チームB
Yanagiさん
Aoyagiさん
Obataさん
さらに、各メンバーに番号を振るなら、以下のようにコードを書くことができます。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

team_a = []
team_b = []

user_list.each.with_index do |user, i|
  if i.odd?
    team_a << user
  else
    team_b << user
  end
end

text = "チームA\n"
# each.with_indexに変更
team_a.each.with_index(1) do |member, i|
  # 各メンバーに番号を振る
  text += "No.#{i}：#{member}さん\n"
end
text += "\nチームB\n"
team_b.each.with_index(1) do |member, i|
  # 各メンバーに番号を振る
  text += "No.#{i}：#{member}さん\n"
end

puts text
実行結果

チームA
No.1：Saitouさん
No.2：Imaiさん
No.3：Takahashiさん


チームB
No.1：Yanagiさん
No.2：Aoyagiさん
No.3：Obataさん
さて、最後に一番肝心なところをリファクタリングしていきましょう。

現在、メンバーのチーム分けは何回やっても同じ結果になってしまいます。これでは面白くないので、メンバーがランダムにチーム分けされるようにしましょう。

その際、配列オブジェクトには便利なメソッドが用意されています。それが、shuffleです。shuffleは、配列の各要素をランダムに並び替えるメソッドです。

以下のようにコードを追加してみましょう。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

# user_listの要素をランダムに入れ替える
user_list.shuffle

team_a = []
team_b = []

user_list.each.with_index do |user, i|
  if i.odd?
    team_a << user
  else
    team_b << user
  end
end

text = "チームA\n"
# each.with_indexに変更
team_a.each.with_index(1) do |member, i|
  # 各メンバーに番号を振る
  text += "No.#{i}：#{member}さん\n"
end
text += "\nチームB\n"
team_b.each.with_index(1) do |member, i|
  # 各メンバーに番号を振る
  text += "No.#{i}：#{member}さん\n"
end

puts text
これで配列の要素はランダムに入れ替えられる処理を書くことができました。しかし、実行結果を見てみましょう。

実行結果

チームA
No.1：Saitouさん
No.2：Imaiさん
No.3：Takahashiさん


チームB
No.1：Yanagiさん
No.2：Aoyagiさん
No.3：Obataさん
なんと、実行結果はshuffleを書く前と変わりません。これはなぜでしょう？

実は、shuffleを実行した時は確かに配列の各要素はランダムに入れ替えられているのですが、その場限りで処理が終わり、元のデータは書き換わってないのです。大切なのは、配列の要素を並び替え、その結果を元データに反映させること。つまり、shuffleの処理結果をきちんとuser_listに反映させないといけないのです。

それを実現するためには、shuffleに!をつけます。そうすると、大元のデータであるuser_listもランダムにシャッフルされた後に元のデータが書き換えられるようになります。

ちなみに、このようなメソッドを破壊的メソッドと呼びます。

user_list = ["Yanagi", "Saitou", "Aoyagi", "Imai", "Obata", "Takahashi"]

# user_listの要素をランダムに入れ替える
user_list.shuffle!

team_a = []
team_b = []

user_list.each.with_index do |user, i|
  if i.odd?
    team_a << user
  else
    team_b << user
  end
end

text = "チームA\n"
# each.with_indexに変更
team_a.each.with_index(1) do |member, i|
  # 各メンバーに番号を振る
  text += "No.#{i}：#{member}さん\n"
end
text += "\nチームB\n"
team_b.each.with_index(1) do |member, i|
  # 各メンバーに番号を振る
  text += "No.#{i}：#{member}さん\n"
end

puts text
実行結果

チームA
No.1：Obataさん
No.2：Imaiさん
No.3：Saitouさん


チームB
No.1：Aoyagiさん
No.2：Yanagiさん
No.3：Takahashiさん
これで、ランダムに各メンバーがチーム分けされるようになりました。

shuffle!のような破壊的なメソッドは、状況に応じて注意して使い分けてください。不用意に使用すると、エラーの原因になることもあります。

繰り返し処理に併せて様々なメソッドが出てきましたが、どれも便利なものばかりなので何度も繰り返し復習して定着させていきましょう。

まとめ
Rubyでは、繰り返し処理にはeachをよく利用します。他の言語では、forやwhileがよく利用されており、実際にRubyにもforやwhileはありますがほとんど使わないので特に勉強しなくて良いでしょう。

できるだけ、無駄を省きながら効率よく勉強されていくと、転職のスピードも早くなるかと思います。ぜひ、ショートカットしながら勉強を進めて行ってください。

お疲れ様でした！