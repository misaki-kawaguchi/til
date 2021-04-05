# ナビゲーション
ユーザーがアプリ内のさまざまなコンテンツ間を移動する操作


[ナビゲーションについて](https://developer.android.com/guide/navigation?hl=ja)

# プラグインを追加
```
plugins {
    id 'androidx.navigation.safeargs.kotlin'
}
```

# build.gradle(:app)ファイルに依存関係を追加
```
dependencies {
  def nav_version = "2.3.4"

  // Kotlin
  implementation "androidx.navigation:navigation-fragment-ktx:$nav_version"
  implementation "androidx.navigation:navigation-ui-ktx:$nav_version"
}
```

[Navigation コンポーネント スタートガイド](https://developer.android.com/guide/navigation/navigation-getting-started?hl=ja)

# build.gradle(:ToDoApp)ファイルにSafe Argsを使用
```
buildscript {
    repositories {
        google()
    }
    dependencies {
        def nav_version = "2.3.4"
        classpath "androidx.navigation:navigation-safe-args-gradle-plugin:$nav_version"
    }
}
```
