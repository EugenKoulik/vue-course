<script setup>
import CardList from "./components/CardList/CardList.vue";
import css from "./App.module.css";
import { reactive, ref, computed } from "vue";

const input = ref("");

const cards = reactive([
  {
    id: 1,
    name: "Anton",
    grade: "Senior",
    salary: 3200,
    currency: "USD"
  },
  {
    id: 2,
    name: "Bogdan",
    grade: "Middle",
    salary: 1800,
    currency: "USD"
  },
  {
    id: 3,
    name: "Denis",
    grade: "Junior",
    salary: 800,
    currency: "USD"
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

