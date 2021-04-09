# linux_and_nginx

## docker起動
### 初回
`$ docker-compose up -d`

### 初回以降
`$ docker-compose start`

## nginx
### 接続
`$ docker-compose exec nginx bash`

### ブラウザ接続
http://localhost:8080

### 作業フォルダ
`./nginx`

## amazonlinux
### 接続
`$ docker-compose exec linux bash`

### 作業フォルダ
`./work`

## linuxコマンド資料
[linuxコマンドについて](docs/linux_command.md)

[linuxコマンドについての練習問題](docs/linux_question.md)

[linuxコマンドについての練習問題の解説](docs/linux_question.md)
