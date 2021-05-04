# 算出プロパティ（computed）

## HTML
```
<div id="app">
   <p>{{ counter }}</p>
   <button @click="counter += 1">+1</button>
   <p>{{ lessThanThree }}</p>
</div>
```

## JavaScript
```
new Vue({
  el: '#app',
  data: {
    counter: 0
  },
  computed: {
    lessThanThree: function() {
      return this.counter > 3 ? '3より上' : '3以下'
    }
  }
})
```

# ComputedとMethodの違い

## HTML(Computedを使う様にする)
```
<div id="app">
   <p>{{ counter }}</p>
   <button @click="counter += 1">+1</button>
   <!-- 参照先の値が変わった時のみ実行される -->
   <p>{{ lessThanThreeComputed }}</p>
   <!-- 再描画されると毎回実行されてしまう -->
   <p>{{ lessThanThreeMethod() }}</p>
</div>
```

## JavaScript
```
new Vue({
  el: '#app',
  data: {
    counter: 0
  },
  computed: {
    lessThanThreeComputed: function() {
      return this.counter > 3 ? '3より上' : '3以下'
    }
  },
  methods: {
    lessThanThreeMethod: function() {
      return this.counter > 3 ? '3より上' : '3以下'
    }
  }
})
```
