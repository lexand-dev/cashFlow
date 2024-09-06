<template>
  <div class="movement">
    <div class="content">
      <h4>{{ title }}</h4>
      <p>{{ description }}</p>
    </div>
    <div class="actions">
      <img src="../assets/close-icon.svg" alt="borrar" @click="remove" />
      <p :class="amountStatus">{{ amountCurrency }}</p>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";

const currencyFormatter = new Intl.NumberFormat("en-US", {
  style: "currency",
  currency: "USD",
});

const { id, amount } = defineProps({
  id: {
    type: Number,
  },
  title: {
    type: String,
    default: "",
  },
  description: {
    type: String,
    default: "",
  },
  amount: {
    type: Number,
  },
});

const amountCurrency = computed(() => {
  return currencyFormatter.format(amount);
});

const amountStatus = computed(() => {
  return amount > 0 ? "green" : "red";
});

const emit = defineEmits(["remove"]);

const remove = () => {
  emit("remove", id);
};
</script>

<style scoped>
.movement {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 16px;
  background-color: #e6f9ff;
  border-radius: 8px;
  box-sizing: border-box;
}
.movement .content {
  width: 100%;
}
.movement .action {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  flex-direction: column;
}
h4,
p {
  margin: 0;
  padding: 0;
}
h4 {
  margin-bottom: 8px;
}
.movement .action img {
  margin-bottom: 16px;
}
.red {
  color: red;
}
.green {
  color: green;
}
</style>
