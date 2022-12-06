<template>
  <div>
    <svg viewBox="0,0 300,200">
      <line
        stroke="#c4c4c4"
        stroke-width="2"
        x1="0"
        :y1="zero"
        x2="300"
        :y2="zero"
      />
      <polyline
        fill="none"
        stroke="#0099fe"
        stroke-width="2"
        :points="puntos"
      />
      <line
        stroke="#0cae00"
        stroke-width="2"
        x1="180"
        y1="0"
        x2="180"
        y2="200"
      />
    </svg>
    <p>Últimos 30 días</p>
  </div>
</template>

<script setup>
import { defineProps, toRefs, computed } from "vue";

const zero = computed(() => {
  return amountToPixels(0);
});

const amountToPixels = (amount) => {
  const min = Math.min(...monthAmount.value);
  const max = Math.max(...monthAmount.value);

  const amountAbsolute = amount + Math.abs(min);
  const minMax = Math.abs(min) + Math.abs(max);

  const sacarPorcentaje = 200 - ((amountAbsolute * 100) / minMax) * 2;

  return sacarPorcentaje;
};

const puntos = computed(() => {
  const total = monthAmount.value.length;
  return monthAmount.value.reduce((puntos, amount, index) => {
    const x = (300 / total) * (index + 1);
    const y = amountToPixels(amount);
    return `${puntos} ${x},${y}`;
  }, "0, 100");
});

const props = defineProps({
  monthAmount: {
    type: Array,
    default: () => [],
  },
});

const { monthAmount } = toRefs(props);
</script>

<style scoped>
svg {
  width: 100%;
  margin-bottom: 20px;
}
p {
  text-align: center;
}
</style>
