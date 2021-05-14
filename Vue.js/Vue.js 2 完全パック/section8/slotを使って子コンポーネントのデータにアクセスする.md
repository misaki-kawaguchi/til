# slotを使って子コンポーネントのデータにアクセスする

## App.vue(親)
```
<template>
  <div>
    <LikeHeader>
      <template v-slot:title="slotProps">
        <h2>こんにちは</h2>
        <h2>{{ slotProps.user.firstName }}</h2>
      </template>
  </div>
</template>
```
v-slot:titleの第一引数に任意の名前をつけると、子コンポーネントのデータにアクセスできる

```
<LikeHeader v-slot="slotProps">
  <p>{{ slotProps }}</p>
  <h2>みなさん</h2>
  <h3>はじめまして</h3>
  <p>よろしくお願いします</p>
</LikeHeader>
```
デフォルトスロットしかない場合は、LikeHeaderにv-slotを書くことができる

## LikeHeader.vue(子)
```
<template>
  <div>
    <slot name="title" :user="user"></slot>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        firstName: 'Jack',
        lastName: 'Donald'
      }
    }
  }
};
</script>
```
`v-bind`で任意の名前をつける（:userは任意の名前、"user"はdataの中のuser）
