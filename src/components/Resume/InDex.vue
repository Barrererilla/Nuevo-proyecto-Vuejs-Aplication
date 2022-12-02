<template>
  <main>
    <p>{{ seeLabel }}</p>
    <h1>{{ seeCurrencyAmount }}</h1>
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
      return this.amount !== null ? this.label : this.date;
    },
    seeCurrencyAmount() {
      return currencyFormatter.format(this.seeAmount);
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
.graphic {
  display: flex;
  width: 100vw;
  justify-content: center;
  align-items: center;
  padding: 48px 24px;
}
</style>
