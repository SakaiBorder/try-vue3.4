<script setup lang="ts">
const count = ref(0)
const isEven = computed(() => count.value % 2 === 0)

watchEffect(() => console.log(isEven.value))

const addCount = () => count.value ++

const setNewCountValue = () => {
  const currentValue = count.value
  count.value = currentValue
}
</script>

<template>
  <div>
    <span>count: {{ count }}</span>
    <button @click="addCount">Add Count</button>
    <button @click="setNewCountValue">Set New Value</button>
  </div>
</template>
