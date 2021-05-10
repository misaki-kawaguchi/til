# v-for

## HTML
```
<div id="app">
  <ul>
    <li v-for="fruit in fruits">{{ fruit }}</li>
  </ul>
</div>
```

## JavaScript
```
new Vue({
  el: '#app',
  data: {
    fruits: ['りんご', 'バナナ', 'ぶどう']
  }
})
```

`・りんご`という風に表示される

## インデックス（番号）を表示する場合

## HTML
```
<div id="app">
  <ul>
    <li v-for="(fruit, index) in fruits">({{ index }}){{ fruit }}</li>
  </ul>
</div>
```

## JavaScript
```
new Vue({
  el: '#app',
  data: {
    fruits: ['りんご', 'バナナ', 'ぶどう']
  }
})
```
`・(0)りんご`という風に表示される

## 第二引数・第三引数を使用する

## HTML
```
<div id="app">
  <ul>
    <li v-for="(value, key, index) in object">{{index}}-{{ value }}</li>
  </ul>
</div>
```

## JavaScript
```
new Vue({
	el: '#app',
  data: {
    object: {
    	firstName: '太郎',
      lastName: '田中',
      age: 21
    }
  }
})
```

## templateタグを使う

## HTML

```
<div id="app">  
  <ul>
    <template v-for="fruit in fruits">
      <li>{{ fruit }}</li>
      <hr>
    </template>
  </ul>
</div>
```

## JavaScript
```
new Vue({
  el: '#app',
  data: {
    fruits: ['りんご', 'バナナ', 'ぶどう']
  }
})
```

リストに下線が引かれる

## 整数値に対してv-forを使用する

## HTML
```
<div id="app">
  <ul>
    <li v-for="n in 10">{{ n }}</li>
  </ul>
</div>
```

## JavaScript
```
new Vue({
  el: '#app'
})
```

1から10までの数字が並ぶ

※inで書かれている箇所はofで書くこともできる

## key属性をつける

## HTML
```
<div id="app">
  <ul>
    <div v-for="fruit in fruits" :key="fruit">
      <p>{{ fruit }}</p>
      <input type="text">
    </div>
  </ul>
  <button @click="remove">先頭を削除</button>
</div>
```

## JavaScript
```
new Vue({
  el: '#app',
  data: {
    fruits: ['りんご', 'バナナ', 'ぶどう']
  },
  methods: {
    remove: function() {
      this.fruits.shift()
    }
  }
})
```

key属性をつけないと、inputの内容がズレてしまう
