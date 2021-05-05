# templateタグを使用して、不必要な要素を加えずにv-ifを複数の要素に適応させる

## HTML
```
<div id="app">
  <template v-if="ok">
    <p>Hello</p>
    <p>Good Bye</p>
    <p>おはよう</p>
  </template>
  <button @click="ok = !ok">ボタン</button>
</div>
```

## Javascript
```
new Vue({
  el: '#app',
  data: {
    ok: true
  }
})
```

ボタンを押すと、テキストは表示・非表示される
