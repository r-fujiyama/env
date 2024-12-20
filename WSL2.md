# WSL2

## インストール

詳細は以下を参照。  
https://learn.microsoft.com/ja-jp/windows/wsl/install

以下を実行すれば`Ubuntu-24.04`がインストールされる。
```powershell
wsl --install -d Ubuntu-24.04
```

## DNS設定

1. DNSを設定する。
    ```shell
    sudo sh -c "echo '[network]\ngenerateResolvConf = false' > /etc/wsl.conf"
    sudo rm /etc/resolv.conf
    sudo sh -c "echo 'nameserver 8.8.8.8' > /etc/resolv.conf"
    ```
1. WSLをシャットダウンする
    ```powershell
    wsl --shutdown
    ```
1. Ubuntu-24.04を起動する。
    ```powershell
    wsl -d Ubuntu-24.04
    ```

## ディストリビューション削除

1. 削除対象ディストリビューション名を確認する。
    ```powershell
    wsl -l -v
    ```
1. ディストリビューションを削除する。
    ```powershell
    wsl --unregister Ubuntu-24.04
    ```

## 備考

-  `wsl -s Ubuntu-20.04`  
既定のディストリビューションを設定。
- `ubuntu2004 config --default-user root`  
デフォルトユーザを root に変更
