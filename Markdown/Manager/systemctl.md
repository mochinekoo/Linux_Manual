# systemctl
* サービスに関するコマンド。

# コマンド
* systemctl daemon-reload ： systemdを更新する（新しくサービスファイルを作った時には、このコマンドを実行する）
* systemctl start サービス名　サービスを開始するコマンド
* systemctl stop サービス名　サービスを停止するコマンド
* systemctl restart サービス名　サービスを再起動するコマンド
* systemctl status サービス名　サービスの状態を確認するコマンド
* systemctl enable サービス名　サービスの自動起動を有効にするコマンド
* systemctl disable サービス名　サービスの自動起動を無効にするコマンド

# serviceファイル（/etc/systemd）
```sh
#!/bin/bash
TMUX_NAME=mcserver

case $1 in
  start)
    tmux new-session -s $TMUX_NAME -d "java -jar spigot-1.12.2.jar";;
  stop)
    sleep 10
    tmux send-keys -t $TMUX_NAME "save-all" Enter
    sleep 5
    tmux send-keys -t $TMUX_NAME "stop" Enter
    sleep 10;;
  *)
    echo "start | stop"
esac
```

```
[Unit]
Description=MinecraftServer
After=network-online.target

[Service]
Type=forking
User=user
WorkingDirectory=/home/user/minecraft/temp
ExecStart=/bin/bash /home/user/minecraft/temp/run.sh start
ExecStop=/bin/bash /home/user/minecraft/temp/rum.sh stop
Restart=always

[Install]
WantedBy=multi-user.target
```
