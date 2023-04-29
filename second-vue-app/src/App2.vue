<script setup>
import { ref } from 'vue';
import Input from './components/Input.vue';
import User from './components/User.vue';

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
  
  <br>
  <br>
  <br>

  <!-- Slotの例 -->
  <User>
    <!-- <span style="font-weight: 900; font-size: 1.4em">John Doe</span> -->
    <template v-slot:title><h1>ユーザ情報</h1></template>
    <template v-slot:content>
      <div>
        <div>
          <div>Jone Doe</div>
          <div>Jane DOe</div>
        </div>
      </div>
    </template>
    <template v-slot:actions><button>ユーザ追加</button></template>

    <template v-slot:scoped="slotProps">
      {{ slotProps.message }}
    </template>
    
    <!-- v-slotは#で省略可能 -->
    <template #default="slotProps">
      {{ slotProps.message }}/{{ slotProps.content }}
    </template>
  
  </User>
</template>

<style scoped></style>