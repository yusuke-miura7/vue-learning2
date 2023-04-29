<script setup>
import { inject } from 'vue';

const message = inject('message');
const reactive_message = inject('reactive_message');
const {count,addCount} = inject('count');
</script>

<template>
<h3>CompBコンポーネント</h3>
<p>{{ message }}</p>
<p>{{ reactive_message }}</p>
<p>Count:{{ count }}</p>
<button @click="addCount">+</button>
</template>