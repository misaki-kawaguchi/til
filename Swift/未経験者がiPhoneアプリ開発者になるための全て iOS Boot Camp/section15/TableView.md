<img width="861" alt="スクリーンショット 2021-07-05 17 57 44" src="https://user-images.githubusercontent.com/60394359/124447117-073d9a80-ddbc-11eb-9edf-2132b789a29f.png">

# NavigationControllerを追加
Editor → Embed In → Navigation Controller を選択する
<img width="763" alt="スクリーンショット 2021-07-05 18 14 49" src="https://user-images.githubusercontent.com/60394359/124448443-6c45c000-ddbd-11eb-9095-afc35159ea0e.png">

# パーツを配置する
<img width="259" alt="スクリーンショット 2021-07-05 18 19 45" src="https://user-images.githubusercontent.com/60394359/124450092-0c501900-ddbf-11eb-9817-8314f0efb74a.png">

# UIViewController（パーツ）を配置
<img width="265" alt="スクリーンショット 2021-07-05 18 30 53" src="https://user-images.githubusercontent.com/60394359/124450193-27228d80-ddbf-11eb-89a3-7c9e5e564604.png">

## Controllerを作成
File → New →　File →　Cocoa Touch Classを選択 → NextViewControllerクラスを作成

## UIViewControllerにNextViewControllerクラスを設定
<img width="260" alt="スクリーンショット 2021-07-05 18 32 57" src="https://user-images.githubusercontent.com/60394359/124450497-710b7380-ddbf-11eb-88a7-0b72a223e0ba.png">

## 画面遷移の設定
controlを押しながらドラッグ → showを選択する

<img width="567" alt="スクリーンショット 2021-07-05 18 39 44" src="https://user-images.githubusercontent.com/60394359/124451666-95b41b00-ddc0-11eb-8ce6-16087cea9a9d.png">

## バックボタンを日本語にする
<img width="945" alt="スクリーンショット 2021-07-05 18 42 26" src="https://user-images.githubusercontent.com/60394359/124452172-1d018e80-ddc1-11eb-830e-576853dc8648.png">

## Identifierを追加する
nextと入力する

<img width="876" alt="スクリーンショット 2021-07-05 18 52 57" src="https://user-images.githubusercontent.com/60394359/124453392-4a9b0780-ddc2-11eb-9872-22bde85e8fe8.png">

# TableViewを構築する
TableView構築に必要なメソッド

・セルの数を決めるメソッド

・セルのセクション数を決めるメソッド

・セルを構築する際に呼ばれるメソッド

・セルの高さを決めるメソッド

・セルがタップされたときに呼ばれるメソッド

## TableViewのデリゲートメソッドを呼べるようにする
・UITableViewDelegate、UITableViewDataSource→TableViewに必要
・numberOfRowsInSectionとcellForRowAtは必須
```
class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {
  @IBOutlet weak var tableView: UITableView!
  
  override func viewDidLoad() {
    super.viewDidLoad()

    // 他のクラスのデリゲートメソッドを自分のクラスで使う
    tableView.delegate = self
    tableView.dataSource = self

  }
    
  // セルの数を確認（必須）
  func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
  }
  
  // セルを構築する（配列の数だけ呼ばれる、必須）
  func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
  }
}
```

## TextFieldを追加
・キーボードを使えるようにしたいので、 UITextFieldDelegateを追加
```
class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource, UITextFieldDelegate {
  @IBOutlet weak var textField: UITextField!
  @IBOutlet weak var tableView: UITableView!
  
  override func viewDidLoad() {
    super.viewDidLoad()

    // 他のクラスのデリゲートメソッドを自分のクラスで使う
    tableView.delegate = self
    tableView.dataSource = self
    textField.delegate = self
  }
    
  // セルの数を確認（必須）
  func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
  }
  
  // セルを構築する（配列の数だけ呼ばれる、必須）
  func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
  }
  
}
```

## TableViewに必要なメソッドを追加
```
class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource, UITextFieldDelegate {
  @IBOutlet weak var textField: UITextField!
  @IBOutlet weak var tableView: UITableView!
  
  // 文字列型が入る配列
  var textArray = [String]()
  
  override func viewDidLoad() {
    super.viewDidLoad()

    // 他のクラスのデリゲートメソッドを自分のクラスで使う
    tableView.delegate = self
    tableView.dataSource = self
    textField.delegate = self
  }
  
  //　①セクションの数を確認
  func numberOfSections(in tableView: UITableView) -> Int {
      return 1
  }
    
  // ②セルの数を確認（必須）
  func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return textArray.count
  }
  
  // ③セルを構築する（配列の数だけ呼ばれる、必須）
  func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    // 再利用可能なcellがあればそれを、なければ新しく作成したcellを返す
    let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath)
        
    // セルのハイライトを消す
    cell.selectionStyle = .none
    // 配列に入っているテキストをセルのテキストに反映する
    cell.textLabel?.text = textArray[indexPath.row]
    cell.imageView!.image = UIImage(named: "checkImage")

    return cell
  }
  
  // セル内のテキストを取得する、画面遷移先にデータを渡す
  func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    // タップしたときにその配列の番号の中身を取り出して、値を渡す
    // nextが画面遷移先
    let nextVC = storyboard?.instantiateViewController(identifier: "next") as! NextViewController

    nextVC.toDoString = textArray[indexPath.row]
    navigationController?.pushViewController(nextVC, animated: true)
  }
  
  // ④1つあたりのセルの高さ
  func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
    return view.frame.size.height / 6
  }
  
  // ⑤キーボードのリターンキーが押されたときに発動される
  func textFieldShouldReturn(_ textField: UITextField) -> Bool {
      textArray.append(textField.text!)
      // キーボードが非表示になる
      textField.resignFirstResponder()
      // テキストを空にする
      textField.text = ""
      // データを更新する
      tableView.reloadData()

      return true
  }
}
```

### TableViewのcellにidentifierを追加

<img width="1171" alt="スクリーンショット 2021-07-05 20 15 56" src="https://user-images.githubusercontent.com/60394359/124463498-f1d16c00-ddcd-11eb-9ed6-3953575d36b6.png">

<img width="859" alt="スクリーンショット 2021-07-05 20 34 57" src="https://user-images.githubusercontent.com/60394359/124465644-9bb1f800-ddd0-11eb-9c82-0c20020b5498.png">

## viewWillAppearを追加
```
class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource, UITextViewDelegate, UITextFieldDelegate {
  何回も呼び出される
  ナビゲーションバーを非表示にする
  override func viewWillAppear(_ animated: Bool) {
      super.viewWillAppear(animated)
      navigationController?.isNavigationBarHidden = true
  }
}

```

```
class NextViewController: UIViewController {

    var toDoString = String()
    @IBOutlet weak var todoLavel: UILabel!
    
    override func viewDidLoad() {
        super.viewDidLoad()

        todoLavel.text = toDoString
    }
    
    // ナビゲーションバーを表示する
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        navigationController?.isNavigationBarHidden = false
    }

}
```
