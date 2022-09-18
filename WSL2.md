# WSL2

## インストール

詳細は以下を参照。  
https://learn.microsoft.com/ja-jp/windows/wsl/install

以下を実行すれば`Ubuntu-20.04`がインストールされる。
```bat
wsl --install
wsl --set-default-version 2
wsl -d Ubuntu-20.04
```

## DNS設定

```sh
sudo sh -c "echo '[network]\ngenerateResolvConf = false' > /etc/wsl.conf"
sudo rm /etc/resolv.conf
sudo sh -c "echo 'nameserver 8.8.8.8' > /etc/resolv.conf"
```

## 備考

-  `wsl -s Ubuntu-20.04`  
既定のディストリビューションを設定。
- `ubuntu2004 config --default-user root`  
デフォルトユーザを root に変更
