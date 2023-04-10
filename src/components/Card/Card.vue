<script setup>
import css from "./Card.module.css";

const  emit = defineEmits(["upCurrency"]);

defineProps({
  name: String,
  grade: String
});

function upCurrencyHandler(employeeName) {
  emit("upCurrency", employeeName);
}
</script>

<template>
 <div :class="css.card">
   <div><strong>Имя : </strong> {{name}} </div>
   <div><strong>Уровень : </strong> {{grade}} </div>
   <div><strong>Зарплата : </strong>
     <slot name="currency"></slot>
   </div>
   <button :class="css.button" @click="upCurrencyHandler(name)">Поднять зарплату!</button>
 </div>
</template>
