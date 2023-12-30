<script setup lang="ts">
const model = defineModel<number>('count', { required: true })

const update = () =>  model.value++
</script>

<template>
  <div>parent bound v-model is: {{ model }}</div>
  <button @click="update">update</button>
</template>
