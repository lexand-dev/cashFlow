<template>
  <main class="resume">
    <p>
      {{ labelVisual }}
    </p>
    <h1>
      {{ amountCurrency }}
    </h1>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<script setup>
import { computed } from "vue";

const { amount, label, totalAmount, totalLabel } = defineProps({
  amount: Number,
  totalAmount: Number,
  label: String,
  totalLabel: String,
});

const amountVisual = computed(() => {
  return amount !== null ? amount : totalAmount;
});

const labelVisual = computed(() => {
  return label !== null ? label : totalLabel;
});

const currencyFormatter = new Intl.NumberFormat("en-US", {
  style: "currency",
  currency: "USD",
});

const amountCurrency = computed(() => {
  return currencyFormatter.format(amountVisual.value);
});
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

h1,
p {
  margin: 0;
  text-align: center;
}

h1 {
  margin-top: 14px;
  color: var(--brand-green);
}

.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>
