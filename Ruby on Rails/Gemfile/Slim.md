# Slimを使えるようにする

Gemfile

```
gem 'slim-rails'
gem 'html2slim'
```

gem 'slim-rails'・・・Slimのジェネレーターを提供

gem 'html2slim'・・・ERB形式のファイルをslim形式に変換してくれるerb2slimコマンドを提供してくれる

```
bundle
```

```
bundle exec erb2slim app/views/layout/ --delete
```
すでに存在しているERB形式のファイルをslim形式に変換

