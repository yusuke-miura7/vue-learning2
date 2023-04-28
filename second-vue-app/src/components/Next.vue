<script setup>
import {ref} from 'vue';
const props = defineProps({
  name: String,
});

const name = ref(props.name);

// scriptタグの中の関数を利用してイベントを発生する際にはdefineEmits関数を利用
// 引数ではイベント名の設定
const emit = defineEmits(['changeNameEvent']);

// 複数の値を渡す
const changeName = () => {
  emit('changeNameEvent', {firstName:'Kevin',lastName: 'James'} );
};

const changeName2 = () => {
  emit('changeNameEvent2', name.value);
};
</script>

<template>
  <h2>子コンポーネント</h2>
  <p>Hello {{ props.name }}</p>
  <button @click="changeName">Change Name</button>
  <p>Hello {{ props.name }}</p>
  <input type="text" v-model="name" @input="changeName2" />
</template>