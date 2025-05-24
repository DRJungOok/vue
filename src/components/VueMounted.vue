<script setup>
import {ref, onMounted} from 'vue'

const pElementRef = ref(null)

onMounted(() => {
  pElementRef.value.textContent = 'onMounted value'
})
</script>

<template>
<p ref="pElementRef">안녕</p>
</template>

<style scoped>

</style>
