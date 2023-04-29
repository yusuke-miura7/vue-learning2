<script setup>
import { ref ,computed ,provide} from 'vue';
import Input from './components/Input.vue';
import User from './components/User.vue';
import Tokyo from './components/Tokyo.vue';
import Kyoto from './components/Kyoto.vue';
import CompA from './components/CompA.vue';

const name = ref('John Doe');
const address = ref('');
const city = ref('tokyo');

const tabs = {
  tokyo: Tokyo,
  kyoto: Kyoto,
}

// X[Y] → オブジェクトXのプロパティ名Yとなっている値を取り出す
const tab = computed( () => tabs[city.value]);

// provide/injectの確認
provide('message', 'Provide/Injectでデータ渡し');
// reactiveな変数も渡してみる
const reactive_message= ref('reactiveな変数をProvide/Injectでデータ渡し');
provide('reactive_message',reactive_message);

// オブジェクトを渡してみる
const count = ref(0);
const addCount = () =>{
  count.value++;
};

provide('count',{
  count,
  addCount,
});

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

    <!-- 子コンポーネントが外部から取得したpropsを表示 -->
    <template v-slot:users="{ user }">
        <li>{{ user.name }}</li>
      </template>
  </User>

  <br>
  <br>
  <br>
  <!-- dynamicコンポーネントの確認 -->
  <div>
    <button @click="city = 'tokyo'">東京</button>
    <button @click="city = 'kyoto'">京都</button>
  </div>
  <div>
    <Tokyo v-if="city =='tokyo'"/>
    <Kyoto v-else/>
  </div>

  <!-- v-bind:isを用いたdynamicコンポーネントの作成 -->
  <component v-bind:is="tab"></component>

  <!-- keep-aliveの確認、動的に切り替えても状態を保持できる -->
  <keep-alive>
    <component v-bind:is="tab"></component>
  </keep-alive>

  <br>
  <br>

  <!-- provide/injectの確認 直接子コンポーネントにpropsを渡せる -->
  <CompA />
  <br>
  <!-- reactiveな変数も渡せることの確認 -->
  <input v-model="reactive_message" />
</template>

<style scoped></style>