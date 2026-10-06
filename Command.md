# その他
* echo 文字を表示するコマンド。スクリプトなど使う。
 * echo "aa" aaと表示される。
 * echo "aa" >> ii.txt　ii.txtにaaと書き込む。
* wget インターネット上からファイルを入手するコマンド
  * wget <URL> でファイルを入手することができる
* less ＜ファイル名＞ ：ファイルをスクロールしながら見る。パイプすると、コマンドの結果にも使える。


# ポート開放
* ufw
* firewall-cmd
 * sudo firewall-cmd --zone=public --add-port=80/tcp --permanent
 * sudo firewall-cmd --reload
