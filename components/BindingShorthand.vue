<script setup lang="ts">
defineProps<{
  id?: string
  name?: string
  alt?: string
}>()
</script>

<template>
  <img :id :name :alt />
</template>
