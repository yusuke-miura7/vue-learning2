<script setup>
import { ref } from 'vue';
import Input from './components/Input.vue';

const name = ref('John Doe');
const address = ref('');
</script>

<template>
  <h1>Vue 3 入門</h1>
  <p>name:{{ name }}</p>
  <p>address:{{ address }}</p>
  <!-- 子コンポーネントから発生するupdate:modelValueイベントを検知するため
    Inputタグに@update:model-valueを追加しnameにemitの引数で設定した
    $event.target.valueを受け取れるように$eventを設定する -->
  <Input :modelValue="name" @update:modelValue="name=$event" />
  <Input :modelValue="address" @update:modelValue="address=$event" />
</template>

<style scoped></style>