# input要素に双方向データバインディングを作成する

## App.vue
```
<div>
  <h2>イベントのフォーム</h2>
  <label for="title">タイトル</label>
  <input id="title" type="text" v-model="eventData.title">
  <p>{{ eventData.title }}</p>
</div>

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
        title: "タイトル"
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
