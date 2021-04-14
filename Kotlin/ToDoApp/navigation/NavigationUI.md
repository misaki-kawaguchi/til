# NavigationUI を使用して UI コンポーネントを更新する

## デフォルトアクションバーにナビゲーションサポートを追加する
①メインアクティビティのonCreate()メソッドから`setupActionBarWithNavController()`を呼び出す
```
setupActionBarWithNavController(findNavController(R.id.navHostFragment))
```


②「上へ」ナビゲーションを処理する onSupportNavigateUp() をオーバーライドする
```
override fun onSupportNavigateUp(): Boolean {
  val navController = findNavController(R.id.navHostFragment)
  return navController.navigateUp() || super.onSupportNavigateUp()
}
```

※navigation/my_nav.xmlのandroid:titleを弄るとナビゲーションのタイトルを変更することができる

[NavigationUI を使用して UI コンポーネントを更新する](https://developer.android.com/guide/navigation/navigation-ui?hl=ja)
