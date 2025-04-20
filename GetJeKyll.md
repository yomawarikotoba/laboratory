---
layout: default
title: 仕様書作成ツール環境構築(Jekyll)
---
# 仕様書作成ツール環境構築(Jekyll)

WindowsとMacの環境構築を記述します。
<br>基本的にはWindowsはWSLでの環境構築となります。
<br>もしかしたらそのうちDocker化するかもしれないです。

## Windows

### 1. WSLとUbuntuのインストール

```sh
wsl --install
```

### 2. Ubuntu内でRubyとJekyllの準備

以下のコマンドをコメントを外した状態でコピペしてください

```sh
sudo apt update # アップデート
sudo apt install -y ruby-full build-essential zlib1g-dev # rubyインストール

# 環境変数登録して実行
echo '# Install Ruby Gems to ~/.gem' >> ~/.bashrc　
echo 'export GEM_HOME="$HOME/.gem"' >> ~/.bashrc
echo 'export PATH="$HOME/.gem/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

# rubyパッケージ管理ツール(gem)でbundlerをインストール
gem install bundler
```

### 3. プロジェクトディレクトリでJekyll起動

```sh
bundle install
bundle exec jekyll serve
```

## macOS

### 1. Homebrewのインストール（未インストールの場合）

Macはzsh想定での構築です。

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. RubyとBundlerのインストール

```bash
brew install ruby
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zprofile
source ~/.zprofile
gem install bundler
```

### 3. プロジェクトディレクトリでJekyll起動

```bash
bundle init
echo 'gem "github-pages", group: :jekyll_plugins' >> Gemfile
bundle install
bundle exec jekyll serve
```
