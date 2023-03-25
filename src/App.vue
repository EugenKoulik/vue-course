<script setup>
import CardList from "./components/CardList.vue";
import css from "./App.module.css";
import { reactive, ref, computed } from "vue";

const input = ref("");

const cards = reactive([
  {
    id: 1,
    name: "Anton",
    description: "QA",
    count: 1200
  },
  {
    id: 2,
    name: "Bogdan",
    description: "Middle",
    count: 1800
  },
  {
    id: 3,
    name: "Denis",
    description: "Junior",
    count: 800
  }
]);

const filteredCards = computed(() => {
  return cards.filter(card => card.name.includes(input.value))
});

</script>

<template>
  <div :class="css.app">
    <input v-model="input"/>
    <CardList :cards="filteredCards"/>
  </div>
</template>

