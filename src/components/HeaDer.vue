<template>
  <header>
    <img src="@/assets/paisaje-azul.svg" alt="Logo" @click="load" />
    <h1><span>Cash</span>Flow</h1>
    <span></span>
  </header>
</template>

<script>
export default {
  methods: {
    load() {
      location.reload();
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-direction: row;
  width: 100vw;
}
img,
span {
  width: 38px;
}
header h1 {
  margin: 0;
  font-weight: bolder;
  color: var(--brand-blue);
  font-size: 25px;
}
header h1 span {
  color: var(--brand-green);
}
</style>
