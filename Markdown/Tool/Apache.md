# インストール
```
sudo apt-get install apahce2
```

* PHPもインストールする場合
```
sudo apt-get install php php-mysql
```

# 設定
* /etc/apahce2/apache2.confで設定
* タグの中に、設定したいディレクティブを書く。その後は ```sudo systemctl restart apache``` で再起動をする
* また、.htaccessファイルを使うことで、ファイルでディレクティブを設定できる。
```
<Directory /var/www/html/PHP_ItemSearch>
  
</Directory>
```

## バーチャルホスト
```
<VirtualHost *:80>
  ServerName aa.example.com
  DocumentRoot /var/www/html/PHP_ItemSearch
</VirtualHost>

<VirtualHost *:80>
  ServerName ii.example.com
  DocumentRoot /var/www/html/PHP_ItemSearch
</VirtualHost>
```

## Require
* 権限許可： Require all granted
* 権限拒否： Require all denied

## AllowOverride
* .htaccess を無視：AllowOverride None
* .htaccess による上書きをすべて許可：AllowOverride All
* 認証・アクセス制御関連の設定許可する：AllowOverride AuthConfig
* ファイル関連の設定を許可する：AllowOverride FileInfo

## Basic認証
```
htpasswd -c 作成する場所 ユーザー名
```

```
AuthType Basic
AuthName "aa"
AuthBasicProvider file
AuthUserFile パスワードの場所
Require valid-user
```
