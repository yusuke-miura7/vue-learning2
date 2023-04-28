<script setup>
import Hello from './components/Hello.vue';

</script>

<template>
  <Hello message="Propsの使い方" name="BEGINNER" />
  <Hello message="defineProps関数を利用" :price="1000"/>
</template>

<style scoped></style>
