<script setup>
import {ref, reactive} from "vue";

const message = ref('hello world');
const dynamicId = ref('dynamicId');
const count = ref(0);
function increment() {
  count.value++;
}
</script>

<template>
  <div>{{message}}</div>
  <div :id="dynamicId">{{dynamicId}}</div>
  <button @click="increment">count value : {{count}}</button>
</template>

<style scoped>
#dynamicId {
  color: red
}
</style>
