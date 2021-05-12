# render関数を使用する

## HTML
```
<div id="app3">
</div>
```

## JavaScript
```
new Vue({
  data: {
    name: '美咲'
  },
  render: function(createElement) {
    return createElement('h1', 'こんにちは、' + this.name);
  }
}).$mount('#app3')
```
