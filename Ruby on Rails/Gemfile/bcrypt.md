# パスワードの入力を受け付けて、digestを生成・保存する

Gemfile
```
gem 'bcrypt', '-> 3.1.7'
```
```
bundle
```

app/models/user.rb
```
class User < ApplicationRecord
  has_secure_password
end
```

モデルの中にhas_secure_passwordを記述すると、データベースのカラムには対応しない属性`password`と`password_confirmation`が追加される。
