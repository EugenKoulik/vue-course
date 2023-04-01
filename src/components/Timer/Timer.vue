<script setup>
import Counter from "../Counter/Counter.vue"
import { ref, watchEffect } from "vue";

const startCountOfSeconds = 140;

let seconds = ref(startCountOfSeconds);
let isRun = ref(false);

watchEffect(() => {
  setInterval(() => {
    if (seconds.value > 0 && isRun.value){
      seconds.value--;
    }
  }, 1000);
});
</script>

<template>
  <div id="timer">
    <h2>Timer</h2>
    <h2>{{ Math.floor(seconds / 60) }}:{{ Math.floor(seconds % 60) }}</h2>
    <button @click="isRun = !isRun">Start/Pause</button>
    <button @click="seconds = startCountOfSeconds">Reset</button>
    <Counter v-bind:counter="seconds"></Counter>
  </div>
</template>