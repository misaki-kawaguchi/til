# $mountメソッドを使用して、elプロパティの代わりにする

## HTML
```
<div id="app">
  <p>{{ message }}</p>
  <p>{{ name }}</p>
  <p>{{ myData }}</p>
  <button @click="message = 'ボタンから変更'">変更</button>
</div>
```

## JavaScript
```
var data = {
  message: 'こんにちは',
  name: '美咲'
}

var vm = new Vue({
  data: data,
  computed: {
    myData: function() {
      return this.$data;
    }
  }
})

vm.$mount('#app')
```
