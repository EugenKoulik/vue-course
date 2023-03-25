<script setup>
import css from "../App.module.css";

defineProps({
  name: String,
  description: String,
  count: Number
});
</script>

<template>
 <div :class="css.card">
   <div><strong>Имя : </strong> {{name}} </div>
   <div><strong>Описание : </strong> {{description}} </div>
   <div><strong>Количество : </strong> {{count}} </div>
 </div>
</template>
