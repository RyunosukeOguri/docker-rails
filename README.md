# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version
2.4.0

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...



## Usage 

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
