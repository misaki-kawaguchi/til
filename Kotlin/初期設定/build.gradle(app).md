# アプリを作る前に色々設定しておく

## id 'kotlin-android-extensions'を追加

下記に追加する
```
plugins {
    id 'com.android.application'
    id 'kotlin-android'
    id 'kotlin-android-extensions'
}
```

インポートできるようになる
```
import kotlinx.android.synthetic.main.activity_main.*
```

これがあると`findViewById`を書かなくてもxmlファイルに書いてあるidを認識してくれる。

## com.google.android.material:material:1.0.0を追加

マテリアルデザインが使えるようになる

```
dependencies {
  // material designが使えるようにする
  implementation 'com.google.android.material:material:1.0.0'
}
```
