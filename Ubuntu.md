# Ubuntu

## 起動

```powershell
wsl -d Ubuntu-24.04
```

## 更新

```shell
sudo apt update
sudo apt upgrade -y
```

## デフォルトエディタを設定

1. デフォルトエディタをvimに変更する。
    ```shell
    sudo update-alternatives --set editor /usr/bin/vim.basic
    ```

## ブランチ名をプロンプトに表示

1. `git-prompt.sh`を`~`にDLする。
    ```shell
    curl -o ~/.git-prompt.sh https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
    ```
1. bash起動時に`.git-prompt.sh`をカレントシェルで実行するように設定する。
    ``` shell
    echo 'source ~/.git-prompt.sh' >> ~/.bashrc
    ```
1. `PS1`を以下の内容に設定する。  
    ``` shell
    echo "PS1='\${debian_chroot:+(\$debian_chroot)}\[\e[1;32m\]\u@\h\[\e[0m\]:\[\e[1;33m\]\w\[\e[1;36m\]\$(__git_ps1)\[\e[0m\]$ '" >> ~/.bashrc
    ```
1. プロンプトを終了する。
    ```shell 
    exit
    ```

## Dockerをインストール

1. 以下のガイドに従いインストールする。  
https://docs.docker.com/engine/install/ubuntu/
1.  ユーザーをdockerグループに所属させる。
    ```shell
    sudo usermod -aG docker $USER
    ```
1. `sudo service docker {run, stop, restart}` 実行時のパスワードを不要にする。
    ```shell
    echo '%docker ALL=(ALL)  NOPASSWD: /usr/sbin/service docker start, /usr/sbin/service docker stop, /usr/sbin/service docker restart' | sudo EDITOR='tee -a' visudo
    ```
1. bash起動時にDockerを起動するように設定する。
    ```shell
    echo -e 'if test $(service docker status | awk '\''{print $4}'\'') = '\''not'\''; then\n    sudo service docker start\nfi' >> ~/.bashrc
    ```
1. プロンプトを終了する。
    ```shell 
    exit
    ```
1. WSLをシャットダウンする。
    ```powershell
    wsl --shutdown
    ```
1. Ubuntu-20.04を起動する。
    ```powershell
    wsl -d Ubuntu-20.04
    ```