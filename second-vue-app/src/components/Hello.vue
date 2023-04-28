<script setup>
import {ref,reactive} from 'vue';
const count = ref(0);
const state = reactive({
    count: 1,
});
</script>

<template>
    <div>
    <h2>初めてのコンポーネント</h2>
    <p>Ref Count:{{ count }}</p>    
    <p>Reactive Count:{{ state.count }}</p>    

    </div>
</template>