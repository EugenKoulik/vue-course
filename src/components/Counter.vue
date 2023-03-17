<script setup>
defineProps({
  counter: Number
})
</script>

<template>
  <div id="counter">
    <h3>Count : {{ counter }}</h3>
    <button @click="counter++">+</button>
    <button @click="counter--">-</button>
  </div>
</template>