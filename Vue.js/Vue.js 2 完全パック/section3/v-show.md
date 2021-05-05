# v-show

## HTML
```
<div id="app">
  <button @click="ok = !ok">ボタン</button>
  <p v-if="ok">If</p>
  <p v-show="ok">Show</p>
</div>
```

## JavaScript
```
new Vue({
  el: '#app',
  data: {
    ok: true
  }
})
```

falseの場合、`v-if`だと要素ごと消える、`v-show`はdisplay: noneとなる
頻繁に切り替える場合は`v-show`を使用する。
※`v-show`はtemplateを使うことはできない。
