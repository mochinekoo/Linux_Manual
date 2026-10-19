# その他
* echo 文字を表示するコマンド。スクリプトなど使う。
 * echo "aa" aaと表示される。
 * echo "aa" >> ii.txt　ii.txtにaaと書き込む。
* wget インターネット上からファイルを入手するコマンド
  * wget <URL> でファイルを入手することができる
* less ＜ファイル名＞ ：ファイルをスクロールしながら見る。パイプすると、コマンドの結果にも使える。
 * ``` history | less ``` 
* wall ＜メッセージ＞ ：ログインしている全員にメッセージを送る
* sleep ＜秒数＞ ：指定した時間の秒数待つ
* history ： コマンドの履歴を見るコマンド
* ssh ： sshで接続するコマンド
  * ```ssh user@127.0.0.1``` ：userというユーザーで、127.0.0.1のサーバーに接続するコマンド
* whoami ： ログインして操作しているユーザー名。userでログインしているなら、userと表示される。


# ポート開放
* ufw
* firewall-cmd
 * sudo firewall-cmd --zone=public --add-port=80/tcp --permanent
 * sudo firewall-cmd --reload

# psコマンド
* プロセスの一覧を表示するコマンド
* ps aux や ps -ef をよく使う。
  * 長いため、```ps aux | less``` で表示するのが良い。

| オプション   | 説明                         |
|--------------|------------------------------|
| オプション無 | 実行中のプロセスが表示される |

| 名前 | 説明                                                                        |
|------|-----------------------------------------------------------------------------|
| PID  | プロセスID。それぞれ重複がないように番号が割り当たっている。                |
| TTY  | プロセスを実行した端末名。制御された端末がない場合は ```?``` と表示される。 |
| TIME | CPUが処理を行った時間。実行時間ではない。                                   |
| CMD  | プロセスの実行コマンド                                                      |

# topコマンド
* CPUなどの使用状態を監視するコマンド

| 名前 | 説明                       |
|------|----------------------------|
| q    | 終了する。                 |
| P    | CPU使用率順に並び変える    |
| M    | メモリ使用率順に並び変える |


# freeコマンド
* メモリの使用状態を確認するコマンド

| 名前 | 説明                       |
|------|----------------------------|
| m、k、g    | 単位を変えて表示する。                 |

| 名前 | 説明                       |
|------|----------------------------|
| total    | メモリの総合                 |
|used|使用メモリー|
|free|空きメモリー|


# Docker
* docker pull ： イメージをダウンロードする
* docker run ：イメージからコンテナを生成し、コマンドを実行する
  *　docker -it ubuntu ： ubuntuを生成する。 
* docker ps ：コンテナ一覧を表示
* docker exec ：実行中のコンテナ内で、新しいプロセスを実行する
  *　```sudo docker exec -it php_itemsearch-php-1 echo "a"``` 
* Dockerfileとcompose.ymlを記述する。
* WORKDIRは、作業する場所で、指定した場所が基準となる。
```Dockerfile
FROM php:8.5-apache
RUN docker-php-ext-install mysqli pdo pdo_mysql
WORKDIR /var/www/html
COPY . /var/www/html 
```
* ポートは、ホスト側（接続する側）：コンテナ側
```yaml
services:
  php:
    build: .
    ports:
      - "8080:80"
    volumes:
      - .:/var/www/html
```
