<script setup>
import css from "./Card.module.css";

defineProps({
  name: String,
  grade: String
});
</script>

<template>
 <div :class="css.card">
   <div><strong>Имя : </strong> {{name}} </div>
   <div><strong>Уровень : </strong> {{grade}} </div>
   <div><strong>Зарплата : </strong>
     <slot name="currency"></slot>
   </div>
 </div>
</template>
