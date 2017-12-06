# README

Docker-composeを使ってRails環境を構築してみました。

* Ruby version
2.4.0
* Heroku version
heroku-cli/6.14.39-addc925 (darwin-x64) node-v9.2.0
* ...


## Usage 

※dockerがない場合は下記URLからインストール
https://docs.docker.com/docker-for-mac/install/
僕はstableの方をインストールしてます。

インストール後バージョンを確認
```
$ docker
Docker version 17.09.0-ce, build afdb6d4

$ docker-compose -v
docker-compose version 1.16.1, build 6d1ac21
```

#### dockerがインストールできたら、このプロジェクトをクローンする
```
$ git clone git@github.com:RyunosukeOguri/docker-rails.git
```

#### mysqlのパスワード設定ファイルをコピー
```
$ cp dokcer/mysql/password.yml.sample dokcer/mysql/password.yml 
```
dokcer/mysql/password.yml
```
version: '2'
services:
  password:
    environment:
      MYSQL_ROOT_PASSWORD: password //これがmysqlのパスワードになります。
```

#### サーバーを起動(rails,mysql)
```
$ docker-compose up もしくは docker-compose up -d
```

#### マイグレーション
```
$ docker-compose run --rm web rake db:migrate
```

#### mysqlに接続
```
$ docker-compose run --rm web rails dbconsole
mysql> select Host, User from mysql.user;
+-----------+-----------+
| Host      | User      |
+-----------+-----------+
| %         | root      |
| localhost | mysql.sys |
| localhost | root      |
+-----------+-----------+
```

#### localhost:3000にブラウザからアクセス

``http://localhost:3000/items``にアクセスしてデーターの新規作成できればOK!


#### サーバーを停止
```
$ docker-compose down
```