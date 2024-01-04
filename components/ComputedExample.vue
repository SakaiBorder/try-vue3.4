<script setup lang="ts">
const fruits = [
  {
    price: 100,
    name: 'apple'
  },
  {
    price: 200,
    name: 'banana'
  },
  {
    price: 300,
    name: 'grape'
  },
  {
    price: 400,
    name: 'lemon'
  },
  {
    price: 500,
    name: 'cherry'
  }
]

const targetPrice = ref(0)

const higherThanTarget1 = computed(() => fruits.filter(fruit => fruit.price > targetPrice.value))

// this always runs because higherThanTarget1 returns new array
watchEffect(() => console.log(`watchEffect1 run: ${higherThanTarget1.value}`))

const higherThanTarget2 = computed<Array<Object>>((lastResult) => {
  const newFiltered = fruits.filter(fruit => fruit.price > targetPrice.value)
  if (lastResult) {
    if (lastResult.length === newFiltered.length) {
      // returns last same array because result is the same
      return lastResult
    }
  }

  return newFiltered
})

// this runs when higherThanTarget2.value changes
watchEffect(() => console.log(`watchEffect2 run: ${higherThanTarget2.value}`))

</script>

<template>
  <div>
    <input v-model="targetPrice" type="number" />
    <div>
      {{ higherThanTarget1 }}
    </div>
    <div>
      {{  higherThanTarget2 }}
    </div>
  </div>
</template>