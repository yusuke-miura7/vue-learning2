<script setup>
import { ref } from 'vue';

const users = ref([]);

const fetchPost = async () => {
  const res = await fetch('https://jsonplaceholder.typicode.com/users');
  users.value = await res.json();
};
fetchPost(); 
</script>

<template>
    <div>
        <slot name="title"></slot>
    </div>
    <div>
        <slot name="content"></slot>
    </div>
    <div>
        <slot name="actions"></slot>
    </div>
    <div>
        <slot name="scoped" message="ユーザ"></slot>

        <slot message="複数のpropsの設定" content="コンテスト"></slot>
        
        <slot name="users" v-for="user in users" :user="user"></slot>
    </div>

</template>