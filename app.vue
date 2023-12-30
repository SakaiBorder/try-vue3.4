<script setup lang="ts">
const bindingProps = {id: "test-id", name: "test-name", alt: "test-alt"}
</script>

<template>
  <div>
    <div>
      <ModelExampleComponent :count="5"/>
    </div>
    <div>
      <BindingShorthand v-bind="bindingProps" />
    </div>
    <div>
      <WatchEffectExample />
    </div>
  </div>
</template>
