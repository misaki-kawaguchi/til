<img width="707" alt="スクリーンショット 2021-07-05 22 03 59" src="https://user-images.githubusercontent.com/60394359/124475715-fe10f580-dddc-11eb-9cd2-df7c146c3459.png">

# ViewController.swift
```
//
//  ViewController.swift
//  Swift6TableViewApp1
//
//  Created by 川口美咲 on 2021/07/05.
//

import UIKit

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {

    @IBOutlet weak var textField: UITextField!
    @IBOutlet weak var tableView: UITableView!
    
    var textArray = [String]()
    var imageArray = ["1", "2", "3", "4", "5"]
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        tableView.delegate = self
        tableView.dataSource = self
    }
    
    // セクションの数
    func numberOfSections(in tableView: UITableView) -> Int {
        return 1
    }
    
    // セルの数を確認（必須）
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return textArray.count
    }
    
    // セルを構築する（配列の数だけ呼ばれる、必須）
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath)
        
        let imageView = cell.contentView.viewWithTag(1) as! UIImageView
        let label = cell.contentView.viewWithTag(2) as! UILabel
        
        label.text = textArray[indexPath.row]
        imageView.image = UIImage(named: imageArray[indexPath.row])
        
        return cell
    }
    
    // セルの高さ
    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        return 524
    }

    // ボタンをタップする
    @IBAction func tap(_ sender: Any) {
        
        if textArray.count > 5 || textField.text?.isEmpty == true {
            // これ以上下に行かせない
            return
        }
        
        textArray.append(textField.text!)
        textField.text = ""
        if textArray.count <= 5 {
            tableView.reloadData()
        }
    }
}
```
