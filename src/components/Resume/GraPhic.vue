<template>
  <div>
    <svg
      viewBox="0,0 300,200"
      @touchstart="tap"
      @touchmove="tap"
      @touchend="untap"
    >
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
        v-if="showLineGreen"
        stroke="#0cae00"
        stroke-width="2"
        :x1="movePointer"
        y1="0"
        :x2="movePointer"
        y2="200"
      />
    </svg>
    <p>Últimos 30 días</p>
  </div>
</template>

<script setup>
import { defineProps, defineEmits, toRefs, computed, ref, watch } from "vue";

const zero = computed(() => {
  return amountToPixels(0);
});

function amountToPixels(amount) {
  const min = Math.min(...monthAmount.value);
  const max = Math.max(...monthAmount.value);

  const amountAbsolute = amount + Math.abs(min);
  const minMoreMax = Math.abs(min) + Math.abs(max);

  const operationToPorcentage = 200 - ((amountAbsolute * 100) / minMoreMax) * 2;

  return operationToPorcentage;
}

const puntos = computed(() => {
  const total = monthAmount.value.length;
  return monthAmount.value.reduce((puntos, amount, index) => {
    const x = (300 / total) * (index + 1);
    const y = amountToPixels(amount);
    return `${puntos} ${x},${y}`;
  }, `0, ${amountToPixels(monthAmount.value.length ? monthAmount.value[0] : 0)}`);
});

const showLineGreen = ref(false);
const movePointer = ref(0);

const emit = defineEmits(["seleccion"]);

watch(movePointer, function (coordenadas) {
  const indice = Math.ceil(coordenadas / (300 / monthAmount.value.length));
  if (indice <= 0 || indice > monthAmount.value.length) {
    return;
  }
  emit("seleccion", monthAmount.value[indice - 1]);
});

const tap = ({ target, touches }) => {
  showLineGreen.value = true;
  const elementWidth = target.getBoundingClientRect().width;
  const elementX = target.getBoundingClientRect().x;
  const touchX = touches[0].clientX;

  movePointer.value = ((touchX - elementX) * 300) / elementWidth;
};

const untap = () => {
  showLineGreen.value = false;
};

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
