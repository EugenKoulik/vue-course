<script setup>
import css from "./CardList.module.css";
import Card from "../Card/Card.vue"
import { ref, reactive, onMounted, onUnmounted } from "vue";

defineProps({
  cards: {
    type: Array
  }
});

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
      <Card
          :name="card.name"
          :grade="card.grade"
      >
        <template #currency>
          <h5>{{Math.round(card.salary * currencies[currentId].coefficient)}} {{currencies[currentId].name}}</h5>
        </template>
      </Card>
    </div>
  </div>
</template>
