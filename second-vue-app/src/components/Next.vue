<script setup>
const props = defineProps({
  name: String,
});

// scriptタグの中の関数を利用してイベントを発生する際にはdefineEmits関数を利用
// 引数ではイベント名の設定
const emit = defineEmits(['changeNameEvent']);

const changeName = () => {
  emit('changeNameEvent');
};
</script>

<template>
  <h2>子コンポーネント</h2>
  <p>Hello {{ props.name }}</p>
  <button @click="changeName">Change Name</button>
</template>