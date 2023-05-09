---
title: "Ubuntu 20.04"
date: 2023-04-25T21:26:00+09:00
---

# WSL2 Ubuntu20.04 環境構築

## 1. 基本設定

```bash
$ cd ~
$ sudo apt update
$ sudo apt install -y \
git \
neovim \
zsh
$ mkdir .ssh
$ mkdir -p src/github.com/$USERNAME # 開発用ディレクトリ作成
$ ssh-keygen -t ed25519 -C "mail@example.com" # 鍵ファイル名はgithub
$ cat github.pub # コピーしてgithubのssh鍵に登録
$ nvim ~/.ssh/config # -> appendix-1を参照
$ chmod 700 ~/.ssh
$ chmod 600 ~/.ssh/config
$ ssh -T github.com # github疎通確認
$ git clone github.com:retty3d/dotfiles.git ~/dotfiles
$ cd ~/dotfiles
$ ./install.sh
```

## 2. WSL2設定

```bash
$ nvim ~/.profile # -> appendix-2を参照
$ exec $SHELL -l
```

## 3. X Window設定

1. VcXsrvをインストールして実行
1. DISPLAY環境変数を設定
```bash
$ nvim ~/.profile # -> appendix-3を参照
$ exec $SHELL -l
$ sudo apt install x11-apps
$ xeyes # 動作確認
```

## Appendix

##### appendix-1: ~/.ssh/config

```ssh_config
ServerAliveInterval 60

Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/github
```

##### appendix-2: ~/.profile

```bash
export SCREENDIR=$HOME/.screen
```

##### appendix-3: ~/.profile
```bash
export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2; exit;}'):0.0
```
