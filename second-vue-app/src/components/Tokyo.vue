<script setup>
import { ref } from 'vue';

const count = ref(0);
</script>

<template>
<h2>東京</h2>
<p>日本の首都です。</p>
<p>{{ count }}</p>
  <button @click="count++">Add Count</button>
</template>