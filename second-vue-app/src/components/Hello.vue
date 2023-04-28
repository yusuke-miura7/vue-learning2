<script setup>
import {ref,reactive} from 'vue';

// 引数の設定
const props = defineProps({
  message:String
})

const count = ref(0);
const state = reactive({
    count: 1,
});

const addRefCount = () =>{
    count.value++;
}

const addReactiveCount = () =>{
    state.count++;
}
</script>

<template>
    <div>
    <h2>初めてのコンポーネント</h2>
    <p>Ref Count:{{ count }}</p>    
    <p>Reactive Count:{{ state.count }}</p>
    <button @click="addRefCount">Ref Count++</button>    
    <button @click="addReactiveCount">Reactive Count++</button>   

    <h3>props</h3>
    <p>{{ props.message }}</p>
    </div>
</template>