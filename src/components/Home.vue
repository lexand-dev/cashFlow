<script setup>
import { computed, reactive, ref } from "vue";

import Action from "./Action.vue";
import Graphic from "./Graphic.vue";
import Header from "./Header.vue";
import Layout from "./Layout.vue";
import Movement from "./Movements.vue";
import Resume from "./Resume.vue";

const movements = ref([
  {
    id: 1,
    title: "Depósito",
    description: "Depósito de nómina",
    amount: 1000,
    type: "ingreso",
  },
  {
    id: 2,
    title: "Retiro",
    description: "Retiro de efectivo",
    amount: -500,
    type: "gasto",
  },
  {
    id: 3,
    title: "Depósito",
    description: "Depósito de nómina",
    amount: 1000,
    type: "ingreso",
  },
  {
    id: 4,
    title: "Retiro",
    description: "Retiro de efectivo",
    amount: -500,
    type: "gasto",
  },
  {
    id: 5,
    title: "Depósito",
    description: "Depósito de nómina",
    amount: 1000,
    type: "ingreso",
  },
  {
    id: 6,
    title: "Retiro",
    description: "Retiro de efectivo",
    amount: -500,
    type: "gasto",
  },
]);

const label = ref(null);
const amount = ref(null);
const amounts = reactive([100, 200, 500, 200, -400, -600, -300, 0, 300, 500]);

const totalAmount = computed(() => {
  return movements.value.reduce((acc, movement) => acc + movement.amount, 0);
});

const create = (movement) => {
  movements.value.push({
    id: new Date().getTime(),
    title: movement.title,
    description: movement.description,
    amount: movement.amount,
    type: movement.typeOfMovement,
  });
  save();
};

const remove = (id) => {
  movements.value = movements.value.filter((movement) => movement.id !== id);
  save();
};
const save = () => {
  localStorage.setItem("movements", JSON.stringify(movements.value));
};

const getMovements = () => {
  const movementsFromLocalStorage = localStorage.getItem("movements");
  if (movementsFromLocalStorage) {
    return (movements.value = JSON.parse(movementsFromLocalStorage));
  }
};

getMovements();
</script>

<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume
        :label="label"
        :amount="amount"
        :totalAmount="totalAmount"
        :totalLabel="'ahorra carajo'"
      >
        <template #graphic>
          <Graphic :amounts="amounts" />
        </template>
        <template #action>
          <Action @create="create" />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movement :movements="movements" @remove="remove" />
    </template>
  </Layout>
</template>
