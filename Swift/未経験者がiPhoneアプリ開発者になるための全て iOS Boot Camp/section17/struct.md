# 画面を作成

・TableView、Cell、TextView、Labelを配置

・Present Modallyで画面遷移するようにする

<img width="618" alt="スクリーンショット 2021-07-06 22 14 32" src="https://user-images.githubusercontent.com/60394359/124608246-865ccc80-dea9-11eb-9c91-19cbd18361b4.png">


# TableViewを実装する
```
//
//  ViewController.swift
//  Swift6Struct2
//
//  Created by 川口美咲 on 2021/07/06.
//

import UIKit

//UITableViewDelegateとUITableViewDataSourceを追加
class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {
    
    @IBOutlet weak var tableView: UITableView!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        tableView.delegate = self
        tableView.dataSource = self
    }
    
    // セルの数を確認（必須）
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 1
    }
    
    // セルを構築する（配列の数だけ呼ばれる、必須）
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        
        let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: IndexPath)
        
        // 型はUILabel
        let userNameLabel = cell.contentView.viewWithTag(1) as! UILabel
        
        let shumiLabel = cell.contentView.viewWithTag(2) as! UILabel
        
        let movieLabel = cell.contentView.viewWithTag(3) as! UILabel
        
        return cell
    }
    
    // セクションの数
    // TableViewがリロードされたタイミングで呼び出される
    func numberOfSections(in tableView: UITableView) -> Int {
        return 1
    }
    
    // セルの高さ
    // TableViewがリロードされたタイミングで呼び出される
    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        return 200
    }
}
```

# 登録ボタンの作成
ボタンを設置して、Identiderに"next"を設定

<img width="941" alt="スクリーンショット 2021-07-08 3 02 54" src="https://user-images.githubusercontent.com/60394359/124807738-0f066600-df99-11eb-8f49-bbdc1354b7cc.png">

## ViewController.swift
```
class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {
  // お気に入りリストを登録する（セグエにより遷移）
  @IBAction func favButton(_ sender: Any) {
    performSegue(withIdentifier: "next", sender: nil)
  }

  // セグエ実行前処理
  override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
    if segue.identifier == "next" {

    }
  }
}
```

# 構造体を作成する

## Person.swift
```
import Foundation

struct Person {
    var name = String()
    var shumi = String()
    var movie = String()
}
```

## NextViewController
```
import UIKit

class NextViewController: UIViewController {
    
    var person = Person()

    override func viewDidLoad() {
        super.viewDidLoad()

    }
}
```

# プロトコルを記載する
ViewControllerにTextFieldで入力したデータを渡すために、プロトコルを作成する

## NextViewController
```
import UIKit

protocol SetOKDelegate {
    // Personクラスが入る
    func setOK(check:Person)
}

class NextViewController: UIViewController {
    
    var person = Person()

    @IBOutlet weak var nameTextField: UITextField!
    @IBOutlet weak var shumiTextField: UITextField!
    @IBOutlet weak var movieTextField: UITextField!
    
    // インスタンス化
    var setOKDelegate:SetOKDelegate?
    
    override func viewDidLoad() {
        super.viewDidLoad()

    }

    // 決定ボタンを押す
    @IBAction func done(_ sender: Any) {
        person.name = nameTextField.text!
        person.shumi = shumiTextField.text!
        person.movie = movieTextField.text!
        setOKDelegate?.setOK(check: person)
        
        dismiss(animated: true, completion: nil)
    }
}
```

## ViewController.swift
```
class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource, SetOKDelegate {

  var person = Person()
  
  // Person型の配列
  var personArray = [Person]()

  func setOK(check: Person) {
      // checkに値が入ってくるので、それを配列に追加する
      personArray.append(check)
      tableView.reloadData()
  }
  
  // セグエ実行前処理
  override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
      if segue.identifier == "next" {

          // デリゲートをどこで実行するかを（委任しなければいけない）
          let nextVC = segue.destination as! NextViewController
          nextVC.setOKDelegate = self
      }
  }
}
```

# Labelのテキストに代入する
## ViewController.swift
```
// セルを構築する（配列の数だけ呼ばれる、必須）
func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {

    let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: IndexPath)

    // 型はUILabel
    let userNameLabel = cell.contentView.viewWithTag(1) as! UILabel
    userNameLabel.text = personArray[indexPath.row].name

    let shumiLabel = cell.contentView.viewWithTag(2) as! UILabel
    shumiLabel.text = personArray[indexPath.row].shumi

    let movieLabel = cell.contentView.viewWithTag(3) as! UILabel
    movieLabel.text = personArray[indexPath.row].movie

    return cell
}
```

# セルの数を修正
```
// セルの数を確認（必須）
func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return personArray.count
}
```
