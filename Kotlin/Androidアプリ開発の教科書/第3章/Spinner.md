# ドロップダウンリストを作成

## strings.xmlに文字列情報を追加
`string-array`タグの中に`item`タグを入れる
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
  <string-array name="sp_currylist">
    <item>ドライカレー</item>
    <item>カツカレー</item>
    <item>ビーフカレー</item>
    <item>チキンカレー</item>
    <item>シーフードカレー</item>
    <item>キーマカレー</item>
    <item>グリーンカレー</item>
  </string-array>
</resources>
```

## レイアウトファイルを編集
`Spinner`タグを使う
```
<?xml version="1.0" encoding="utf-8"?>
<LinerLayout>
~省略〜
  <Spinner
  android:id="@+id/suCurryList"
  android:layout_width="match_parent"
  android:layout_height="wrap_content"
  android:background="fff"
  android:entries="@array/sp_currylist"
  android:paddingBottom="5dp"
  android:paddingTop="5dp"/>
  ~省略~
```
