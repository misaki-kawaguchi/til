# 「Action」ボタンをタップすると画像の扱い方に関する選択肢が表示され、各アイコンをタップすることで、画像を送信したり、保存したりする。

imageView:画像
showActivityView：ボタン

```
@IBOutlet weak var imageView: UIImageView!
@IBAction func showActivityView(_ sender: UIBarButtonItem) {
  let controller = UIActivityViewController(activityItems: [imageView.image!], applicationActivities: nil)　・・・①
  self.present(controller, animated: true, completion: nil)　・・・②
}
```

①ストーリーボードに追加したイメージビューに表示している画像を引数にして、UIActivityViewControllerクラスのインスタンスを作成し、定数controllerに格納する。
|  引数（ラベル）  |  内容  |
| ---- | ---- |
|  activityItems  |  動作の対象となるコンテンツ（文字列や画像など）を配列で指定する。引数の型は配列なので複数のコンテンツを指定できる。  |
|  applicationActivities  |  UIActivityViewControllerクラスがデフォルトでサポートしていないWebサービスなどに画像を投稿する場合に、その処理を配列で指定する。特に何も指定しない場合は「nil」を指定する。  |



②controller（インスタンス）をモーダルビューコントローラとして表示する
### present(_:animated:completion)メソッド
モーダルビューコントローラーをpresent(_:animated:completion)メソッドの引数の引数に指定する
→自身が持つviewプロパティを画面上に表示する

|  引数（ラベル）  |  内容  |
| ---- | ---- |
|  -  |  ビューコントローラーを指定する。 |
|  animated  |  モーダルビューをアニメーションで表示するか否か指定する。  |
|  completion  |  モーダルビューの表示が完了した後に追加で何らかの処理を実行したい場合はここにクロージャを指定する。処理が必要ない場合は「nil」を指定する。  |
