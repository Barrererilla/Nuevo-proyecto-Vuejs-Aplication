<template>
  <main class="parent-main">
    <p>{{ seeLabel }}</p>
    <h1 :class="{ green: colorCurrency, red: !colorCurrency }">
      {{ seeCurrencyAmount }}
    </h1>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<script>
const currencyFormatter = new Intl.NumberFormat("es-CO", {
  style: "currency",
  currency: "COP",
});

export default {
  data() {
    return {};
  },
  props: {
    label: {
      type: String,
    },
    amount: {
      type: Number,
      default: null,
    },
    fullAmount: {
      type: Number,
    },
    date: {
      type: String,
    },
  },
  computed: {
    seeAmount() {
      return this.amount !== null ? this.amount : this.fullAmount;
    },
    seeLabel() {
      return this.amount !== null ? this.date : this.label;
    },
    seeCurrencyAmount() {
      return currencyFormatter.format(this.seeAmount);
    },
    colorCurrency() {
      return this.fullAmount > 0;
    },
  },
};
</script>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100vw;
  margin-bottom: 60px;
}
main h1,
p {
  margin: 0;
  text-align: center;
}
main p {
  color: rgb(64, 64, 64);
}
main h1 {
  color: green;
  font-weight: bolder;
  font-size: 50px;
}
.red {
  color: rgb(148, 38, 38);
}
.green {
  color: green;
}
.graphic {
  display: flex;
  width: 100vw;
  justify-content: center;
  align-items: center;
  padding: 48px 24px;
}
</style>
