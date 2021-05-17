# ⑩コンポーネントでv-modelを使う方法

## App.vue(親)
```
<template>
  <div>
    <h2>イベントのフォーム</h2>
    <EventTitle v-model="eventData.title"></EventTitle>
  </div>
</template>

<script>
import EventTitle from "./components/EventTitle.vue";

export default {
  data() {
    return {
      eventData: {
        title: ""
    };
  },
  components: {
    EventTitle
  }
};
</script>


```

## EventTitle.vue(子)
```
<template>
  <div>
    <label for="title">タイトル</label>
    <input
      id="title"
      type="text"
      :value="value"
      @input="$emit('input', $event.target.value)"
    >
    <pre>{{ eventData.title }}</pre>
  </div>
</template>

<script>
export default {
  props: ["value"]
}
</script>
```
