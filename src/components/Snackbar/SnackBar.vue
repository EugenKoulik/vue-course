<script setup>
import { Transition } from "vue";
import css from "./SnackBar.module.css"

const emit = defineEmits(["close"]);
const props = defineProps({
  id: Number,
  message: String,
  delay: Number
});

function closeHandler(id) {
  emit("close", id);
}

</script>

<template>
  <Transition name="snack" appear>
    <div :class="css.snack_bar">
      <h5> {{ message }} </h5>
      <button :class="css.snack_bar__times" @click="closeHandler(props.id)">&times;</button>
    </div>
  </Transition>
</template>

<style scoped>

.snack-enter-active,

.snack-leave-active {
  transition: 400ms;
}

.snack-enter-from {
  opacity: 0;
  transform: translateX(-100%);
}

.snack-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}
</style>
