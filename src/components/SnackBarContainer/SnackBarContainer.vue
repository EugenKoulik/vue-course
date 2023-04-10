<script setup>
import SnackBar from "../Snackbar/SnackBar.vue";
import { Teleport } from "vue";

const emit = defineEmits(["close"]);

defineProps({
  snacks: Array
})

function closeHandler(id) {
  emit("close", id)
}
</script>

<template>
  <Teleport to="#snack-bar-container">
    <div v-for="snack in snacks">
      <SnackBar
          @close="closeHandler"
          :id="snack.id"
          :delay="snack.delay"
          :message = "snack.message"
      ></SnackBar>
    </div>
  </Teleport>
</template>
