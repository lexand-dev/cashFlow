<template>
  <div>
    <svg viewBox="0 0 300 200">
      <line
        x1="0"
        y1="100"
        x2="300"
        y2="100"
        stroke="#c4c4c4"
        stroke-width="2"
      />
      <polyline
        :points="points"
        fill="none"
        stroke="#0689B0"
        stroke-width="2"
      />
      <line
        x1="200"
        y1="0"
        x2="200"
        y2="200"
        stroke="#04b500"
        stroke-width="2"
      />
    </svg>
    <p>Últimos 30 días</p>
  </div>
</template>

<script setup>
import { computed } from "vue";

const { amounts } = defineProps({
  amounts: {
    type: Array,
    default: () => [],
  },
});

const amountToPixels = (amount) => {
  const min = Math.min(...amounts);
  const max = Math.max(...amounts);

  const amountAbs = amount + Math.abs(min);
  const minmax = Math.abs(max) + Math.abs(min);

  return 200 - ((amountAbs * 100) / minmax) * 2;
};

const zero = computed(() => {
  return amountToPixels(0);
});

const points = computed(() => {
  const total = amounts.length;
  return amounts.reduce((points, amount, i) => {
    const x = (300 / total) * (i + 1);
    const y = amountToPixels(amount);
    return `${points} ${x},${y}`;
  }, "0, 100");
});
</script>

<style scoped>
svg {
  width: 100%;
}
p {
  text-align: center;
}
</style>
