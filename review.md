# Laravel Lesson レビュー①

## Todo一覧機能

### Todoモデルのallメソッドで実行しているSQLは何か

SELECT文。

### Todoモデルのallメソッドの返り値は何か

illuminate\Database\Eloquent\Collectionクラスのインスタンスが返り値となっている。

### 配列の代わりにCollectionクラスを使用するメリットは

Collectionクラスは配列の操作に特化したクラスで、インスタンスとして変数に代入し値を渡すなどのことができるから。

### view関数の第1・第2引数の指定と何をしているか

第一引数に表示させたいBladeファイルを指定し、第二引数には連想配列で、blade内の変数に対して、画面に表示させたいデータを渡している。

### index.blade.phpの$todos・$todoに代入されているものは何か

$todosにはCollectionインスタンスが入っていて、$todoにはCollectionインスタンスに格納されていたTodoインスタンスが入っている。

## Todo作成機能

### Requestクラスのallメソッドは何をしているか

入力フォームから送信された値を連想配列の形で取得している。

### fillメソッドは何をしているか

fillメソッドの引数に入っている値のバリューをメソッド実行元の要素に代入している。

### $fillableは何のために設定しているか

一括代入には脆弱性があるため、攻撃者のフォーム改ざんによる不正データの送信時に、fillableで定めていない値は再代入できないように設定する必要があるから。

### saveメソッドで実行しているSQLは何か

INSERT文。

### redirect()->route()は何をしているか

routeメソッドで得られたURL情報をredirectメソッドに送り、そのURLへ飛ぶようにしている。

## その他

### テーブル構成をマイグレーションファイルで管理するメリット

マイグレーションファイルでテーブルを管理する場合、開発者チーム全員で同じテーブルをファイル1つで共有することができるため

### マイグレーションファイルのup()、down()は何のコマンドを実行した時に呼び出されるのか

Up()は php artisan migrate, down()は php artisan migrate:rollback

### Seederクラスの役割は何か

Seederファイル内で作成したテストデータを、データベース上に反映させること。

### route関数の引数・返り値・使用するメリット

route関数の引数には事前に定義づけられたルート名が入り、その返り値はそのルートで設定したURLが返される、これによって、個別にURLを書かずに呼び出すことができるので保守性が上がる。

### @extends・@section・@yieldの関係性とbladeを分割するメリット

extendsが各Bladeで共通している記述を束ねた親bladeを指定しており、sectionが個別に残った記述の終わりと始まりを場所で示している。yieldは親blade内に存在しており、sectionと同じ引数をyieldにも渡すことで、それぞれを紐づけることができる。これによって、保守性の高い記述になる。

### @csrfは何のための記述か

クロスサイトリクエストフォージェリの手法を使った攻撃から守るため。

### {{ }}とは何の省略系か

<?php echo ~~ ?>、{{}}の場合だとエスケープ処理も同時に行って出力される。