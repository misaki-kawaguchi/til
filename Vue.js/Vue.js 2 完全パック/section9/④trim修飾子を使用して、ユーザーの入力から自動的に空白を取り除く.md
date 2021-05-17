# ④trim修飾子を使用して、ユーザーの入力から自動的に空白を取り除く

## App.vue
```
<template>
  <div>
    <label for="host">主催者</label>
    <input id="host" type="text" v-model.trim="eventData.host">
    <pre>{{ eventData.host }}</pre>
  </div>
</template>

<script>
import LikeHeader from "./components/LikeHeader.vue";
import About from "./components/About.vue";
import Home from "./components/Home.vue";

export default {
  data() {
    return {
      number: 10,
      currentComponent: "Home",
      eventData: {
        title: "タイトル",
        maxNumber: 0,
        host: ""
    };
  },
  components: {
    LikeHeader,
    About,
    Home
  }
};
</script>
```

`<pre></pre>`はテキストの一番前と後ろのスペースを改行を反映させる。
trim修飾子を使うことで、スペースを取り除いてくれる。
