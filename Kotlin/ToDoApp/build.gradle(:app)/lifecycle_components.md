# Lifecycle
ライフサイクル対応コンポーネントは、別のコンポーネント（アクティビティやフラグメントなど）のライフサイクルステータスの変化に対応してアクションを実行します。

これらのコンポーネントを使用することで、適切に整理されメンテナンスが容易な軽量のコードを作成できます。

# build.gradle(:app)ファイルに依存関係を追加
```
implementation "androidx.lifecycle:lifecycle-extensions:2.2.0"
implementation "androidx.lifecycle:lifecycle-common-java8:2.3.0"
implementation "androidx.lifecycle:lifecycle-viewmodel-ktx:2.3.0"
```

[Lifecycleについて](https://developer.android.com/jetpack/androidx/releases/lifecycle?hl=ja)
