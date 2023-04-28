<script setup>
import Hello from './components/Hello.vue';
import { ref } from 'vue';

const name = ref('Mike');
const changeName = () =>{
  name.value = 'Bob';
}
</script>

<template>
  <Hello message="Propsの使い方" name="BEGINNER" />
  <br>
  <Hello message="defineProps関数を利用" :price="1000" :isAdmin="true"/>
  <br>
  <Hello message="reactiveな変数を渡す" :name="name" />
  <button @click="changeName">Change Name</button>

</template>

<style scoped></style>
