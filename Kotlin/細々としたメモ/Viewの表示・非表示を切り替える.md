# Viewの表示・非表示を切り替える

| 引数 | 説明 |
|:-----------|:------------|
| View.VISIBLE       | 表示する。これが初期値。        | 
| View.INVISIBLE     | 非表示にする。非表示にした領域は詰めない。viewが見えないだけで、領域は占める。CSSのvisibility:hiddenに似ている。   | 
| View.GONE       | 非表示にする。非表示にした領域を詰める。viewがそもそもなかったように振舞う。CSSのdisplay:noneに似ています。        | 


下記のように入力する
```
editText.visibility = View.VISIBLE
doneButton.visibility = View.VISIBLE
view.visibility = View.GONE
```
