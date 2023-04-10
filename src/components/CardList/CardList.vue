<script setup>
import css from "./CardList.module.css";
import Card from "../Card/Card.vue"
import SnackBarContainer from "../SnackBarContainer/SnackBarContainer.vue";

import { ref, reactive, onMounted, onUnmounted } from "vue";

defineProps({
  cards: {
    type: Array
  },
  filterString: {
    type: String
  }
});

const DELAY = 3000;

const currentId = ref(0);
const interval = ref(0);
const currencies  = reactive([
  {
    id: 0,
    name: "EUR",
    coefficient: 0.919901
  },
  {
    id: 1,
    name: "RUB",
    coefficient: 78.000119
  },
  {
    id: 2,
    name: "USD",
    coefficient: 1
  },
]);
const snacks = reactive([]);

function upCurrency(name) {

  const now = new Date();

  let newSnack = {
    id: now.getTime(),
    message: name + " просит повышение!",
    delay: DELAY
  }
  snacks.push(newSnack);
}

function closeSnack(id) {
  snacks.splice(snacks.find(snack => snack.id === id), 1);
}

onMounted(() => {

  interval.value = setInterval( () => {

    currentId.value++;

    if (currentId.value >= currencies.length) {

      currentId.value = 0;
    }
  }, 3000);
});

onUnmounted(() => {
  clearInterval(interval.value);
});
</script>

<template>
  <div :class="css.cardList">
    <div v-for="card in cards" :key="card.id">
      <Card @up-currency="upCurrency"
          v-if="card.name.includes(filterString)"
          :name="card.name"
          :grade="card.grade">
        <template #currency>
          <span>{{ Math.round(card.salary * currencies[currentId].coefficient) }} {{ currencies[currentId].name }}</span>
        </template>
      </Card>
    </div>
    <SnackBarContainer @close="closeSnack" :snacks="snacks"/>
  </div>
</template>
