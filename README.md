Wordpress base project
====
## Description
- docker composeでWordpressのベースを構築する
- memcachedを使えるようにする
- proxy用にdocument rootを設定できるようにする

## Configure
- .envを作成する
```
# wordpressの設定
WORDPRESS_DB_NAME=wordpressのデータベース名
WORDPRESS_DB_USER=wordpressのDBユーザ名
WORDPRESS_DB_PASSWORD=DBユーザのパスワード
WORDPRESS_DOCUMENT_ROOT=wordpressを設置するドキュメントルート

# mysqlの設定
MYSQL_RANDOM_ROOT_PASSWORD=yes #rootのパスワードをランダムなパスワードにするか
MYSQL_DATABASE=作成するデータベース名(WORDPRESS_DB_NAMEと同じ)
MYSQL_USER=作成するユーザ名(WORDPRESS_DB_USERと同じ)
MYSQL_PASSWORD=作成するユーザのパスワード(WORDPRESS_DB_PASSWORDと同じ)

# phpmyadminの設定
PMA_ARBITRARY=1
PMA_HOST=db
PMA_USER=作成したMySQLのユーザ名(MYSQL_USERと同じ)
PMA_PASSWORD=作成したユーザのパスワード(MYSQL_PASSWORDと同じ)
```

## Usage
- `docker-compose up -d` を実行。サイトにアクセス出来るようになるまでは少し時間がかかる
- ./www_data がWordpressのルートとなる。ホスト側で編集できる。
- `http://localhost:9000`にアクセスしてWordpressのセットアップ画面になれば完了。
- `http://localhost:8080`にアクセスすると、phpmyadminに接続出来る。
- `mysql -h 127.0.0.1 -P 33060 -u DBユーザ名 -p`でmysqlコマンドでDBに接続出来る。
- なんとなくバックエンドとして動作することを想定しているので、各ポートが外部に出ないようにご注意ください。

## Licence
- [MIT](https://github.com/loopsketch/wp-base/blob/master/LICENSE.txt)

## Author
[loopsketch](https://github.com/loopsketch)
