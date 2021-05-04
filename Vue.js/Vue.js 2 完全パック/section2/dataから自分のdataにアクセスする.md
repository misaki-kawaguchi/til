# dataから自分のdataにアクセスする

## HTML
```
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.12/dist/vue.js"></script>

  <div id="app">
    <p>{{ sayHi() }}</p>
  </div>
```

## JavaScript（thisを使ってアクセスする）
```
new Vue({
  el: '#app',
  data: {
    message: 'Hello World!'
  },
  methods: {
    sayHi: function() {
      return this.message
    }
  }
})
```
