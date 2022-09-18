# Ubuntu

## 起動

```bat
wsl -d Ubuntu-20.04
```

## 更新

```sh
sudo apt update
sudo apt upgrade
```

## デフォルトエディタを設定

1. デフォルトエディタ変更画面を表示する。
    ```sh
    sudo update-alternatives --config editor
    ```
1. `/usr/bin/vim.basic`を選択する。

## ブランチ名をプロンプトに表示

1. `git-prompt.sh`を`~`にDLする。
    ```sh
    curl -o ~/.git-prompt.sh https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
    ```
1. bash起動時に`.git-prompt.sh`をカレントシェルで実行するように設定する。
    ``` sh
    echo 'source ~/.git-prompt.sh' >> ~/.bashrc
    ```
1. `~/.bashrc`の`if [ "$color_prompt" = yes ]; then`の下に存在する`PS1`を以下に書き換える。  
    ``` sh
    PS1='${debian_chroot:+($debian_chroot)}\[\e[1;32m\]\u@\h\[\e[0m\]:\[\e[1;33m\]\w\[\e[1;36m\]$(__git_ps1)\[\e[0m\]$ '
    ```
1. プロンプトを終了する。
    ```sh 
    exit
    ```
1. WSLをシャットダウンする。
    ```bat
    wsl --shutdown
    ```
1. Ubuntu-20.04を起動する。
    ```bat
    wsl -d Ubuntu-20.04
    ```

## Dockerをインストール

1. 以下のガイドに従いインストールする。  
https://docs.docker.com/engine/install/ubuntu/
1.  ユーザーをdockerグループに所属させる。
    ```sh
    sudo usermod -aG docker $USER
    ```
1. `sudo service docker {run, stop, restart}` 実行時のパスワードを不要にする。
    ```sh
    echo '%docker ALL=(ALL)  NOPASSWD: /usr/sbin/service docker start, /usr/sbin/service docker stop, /usr/sbin/service docker restart' | sudo EDITOR='tee -a' visudo
    ```
1. bash起動時にDockerを起動するように設定する。
    ```sh
    echo -e 'if test $(service docker status | awk '\''{print $4}'\'') = '\''not'\''; then\n    sudo service docker start\nfi' >> ~/.bashrc
    ```
1. プロンプトを終了する。
    ```sh 
    exit
    ```
1. WSLをシャットダウンする。
    ```bat
    wsl --shutdown
    ```
1. Ubuntu-20.04を起動する。
    ```bat
    wsl -d Ubuntu-20.04
    ```