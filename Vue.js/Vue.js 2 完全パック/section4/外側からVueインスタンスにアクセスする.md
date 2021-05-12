# 外側からVueインスタンスにアクセスする

ボタンをクリックすると、#app1のテキストが変わる

## HTML
```
<div id="app1">
  <p>{{ message }}</p>
</div>

<div id="app2">
  <p>{{ message }}</p>
  <button @click="changeMessage1">インスタンス1のメッセージを変更</button>
</div>
```

## JavaScript
```
var vm1 = new Vue({
  el: '#app1',
  data: {
    message: 'インスタンス１'
  }
})

var vm2 = new Vue({
  el: '#app2',
  data: {
    message: 'インスタンス2'
  },
  methods: {
    changeMessage1: function() {
      vm1.message = 'インスタンス2から変えました'
    }
  }
})
```
