# $emitメソッドを使って、子から親にデータを渡す

## App.vue(親)

```
<template>
  <div>
    <LikeHeader></LikeHeader>
    <h2>{{ number }}</h2>
    <LikeNumber :number="number" @my-click="number = $event"></LikeNumber>
    <LikeNumber :number="6"></LikeNumber>
  </div>
</template>

<script>
import LikeHeader from "./components/LikeHeader.vue";

export default {
  data() {
    return {
      number: 10
    }
  },
  components: {
    LikeHeader
  }
};
</script>
```

## LikeNumber.vue(子)
```
<template>
  <div>
    <p>いいね({{ halfNumber }})</p>
    <button @click="increment">+1</button>
  </div>
</template>

<script>
export default {
  props: {
    totalNumber: {
      type: Number,
      required: true
    }
  },
  computed: {
    halfNumber() {
      return this.totalNumber / 2;
    }
  },
  methods: {
    increment() {
      this.$emit("my-click", this.totalNumber + 1);
    }
  }
};
</script>
```

※カスタムイベント名はケバブケースにする
