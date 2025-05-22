<script setup>
import {ref, reactive} from "vue";

const message = ref('hello world');
const dynamicId = ref('dynamicId');
const counter = reactive({
  count: 0
})

console.log(counter.count);
counter.count++;
</script>

<template>
  <div>{{message}}</div>
  <div :id="dynamicId">{{dynamicId}}</div>
</template>

<style scoped>
#dynamicId {
  color: red
}
</style>
