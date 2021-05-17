# textareaにv-modelを使用して、複数行テキストに双方向データバインディングする

## App.vue
```
<template>
  <div>
    <label for="detail">イベントの内容</label>
    <texrarea id="detail" cols="30" rows="10" v-model="eventData.detail"></texrarea>
    <pre>{{eventData.detail}}</pre>
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
        title: "",
        maxNumber: 0,
        host: "",
        detail: ""
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
