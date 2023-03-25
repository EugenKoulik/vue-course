<script setup>
import css from "../App.module.css";
import Card from "./Card.vue"

defineProps({
  cards: {
    type: Array
  }
})
</script>

<template>
  <div :class="css.cardList">
    <div v-for="card in cards" :key="card.id">
      <Card
          :name="card.name"
          :description="card.description"
          :count="card.count"
      ></Card>
    </div>
  </div>
</template>
