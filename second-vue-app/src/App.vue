<script setup>
import Hello from './components/Hello.vue';
import Next from './components/Next.vue';

import { ref } from 'vue';

const name = ref('Mike');
const changeName = () =>{
  name.value = 'Bob';
}

const handleEvent = (newName) => {
  console.log('子コンポーネントからの通知');
  name.value = `${newName.firstName} ${newName.lastName}`;
}

const handleEvent2 = (newName) => {
  console.log('子コンポーネントからの通知');
  name.value = newName;
};

</script>

<template>
  <Hello message="Propsの使い方" name="BEGINNER" />
  <br>
  <Hello message="defineProps関数を利用" :price="1000" :isAdmin="true"/>
  <br>
  <Hello message="reactiveな変数を渡す" :name="name" />
  <button @click="changeName">Change Name</button>
  <br>

  <!-- <Next v-on:notification="handleEvent"/> -->
  <Next @changeNameEvent="handleEvent" 
  @changeNameEvent2="handleEvent2" 
  :name="name" />

</template>

<style scoped></style>
