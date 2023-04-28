<script setup>
import {ref,reactive} from 'vue';

// 引数の設定
const props = defineProps({
    price: {type:Number, default: 500},
    message:{type: String, required: true},
    name:{type: String, default: 'John'},
    isAdmin: Boolean,
});

// ref,reactive関数の実装
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
    <p>{{ props.name }}</p>
    <p>{{ props.price +100}}</p>
    <p v-if="props.isAdmin">管理者です。</p>
    <p v-else>管理者ではありません。</p>
    </div>
</template>