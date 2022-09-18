# Ubuntu

## 起動

1. `wsl -d Ubuntu-20.04`

## 更新

1. `sudo apt update`
1. `sudo apt upgrade`

## デフォルトエディタを設定

1. `sudo update-alternatives --config editor`
1. `/usr/bin/vim.basic`を選択する。

## ブランチ名をプロンプトに表示

1. `curl -o ~/.git-prompt.sh https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh`
1. `echo 'source ~/.git-prompt.sh' >> ~/.bashrc`
1. `~/.bashrc`の`if [ "$color_prompt" = yes ]; then`の下に存在する`PS1`を以下に書き換える。  
`PS1='${debian_chroot:+($debian_chroot)}\[\e[1;32m\]\u@\h\[\e[0m\]:\[\e[1;33m\]\w\[\e[1;36m\]$(__git_ps1)\[\e[0m\]$ '`
1. `exit`
1. `wsl -d Ubuntu-20.04`

## Dockerをインストール

1. 以下のガイドに従いインストールする。  
https://docs.docker.com/engine/install/ubuntu/
1. `sudo usermod -aG docker $USER`
1. `echo 'sudo /etc/init.d/docker start' >> ~/.bashrc`
1. `echo '%docker ALL=(ALL)  NOPASSWD: /etc/init.d/docker' | sudo EDITOR='tee -a' visudo`
1. `exit`
1. `wsl -d Ubuntu-20.04`