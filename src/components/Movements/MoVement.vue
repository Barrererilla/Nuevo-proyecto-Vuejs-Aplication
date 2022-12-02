<template>
  <div class="movement">
    <div class="contain">
      <h4>{{ title }}</h4>
      <p>{{ descripcion }}</p>
    </div>
    <div class="action">
      <img src="@/assets/basurero.svg" alt="borrar" @click="remove" />
      <p :class="{ red: !seeColorCurrency, green: seeColorCurrency }">
        {{ currencyAmount }}
      </p>
    </div>
  </div>
</template>

<script setup>
import { defineEmits, defineProps, toRefs, computed } from "vue";

const currencyFormatter = new Intl.NumberFormat("es-CO", {
  style: "currency",
  currency: "COP",
});

const currencyAmount = computed(() => {
  return currencyFormatter.format(moneyAmount.value);
});

const seeColorCurrency = computed(() => {
  return moneyAmount.value > 0;
});

const props = defineProps({
  title: {
    type: String,
  },
  descripcion: {
    type: String,
  },
  identificador: {
    type: Number,
  },
  moneyAmount: {
    type: Number,
  },
});

const emit = defineEmits(["remove"]);

const remove = () => {
  emit("remove", identificador.value);
};

const { title, descripcion, identificador, moneyAmount } = toRefs(props);
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
  gap: 10px;
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
  color: rgb(43, 0, 0);
}
h4 {
  margin-bottom: 8px;
  font-weight: bolder;
  color: rgb(113, 111, 111);
}
.movement .action img {
  margin-bottom: 16px;
}
.green {
  color: rgb(52, 221, 52);
}
.red {
  color: rgb(175, 50, 50);
}
</style>
