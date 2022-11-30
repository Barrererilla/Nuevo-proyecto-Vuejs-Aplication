<template>
  <div class="splashscreen">
    <img src="@/assets/paisaje-azul.svg" alt="Logo" />
    <h1><span>Cash</span>Flow</h1>
    <div class="reload">Cargando...</div>
  </div>
</template>

<style scoped>
.splashscreen {
  display: flex;
  align-items: center;
  flex-direction: column;
  height: 100vh;
  justify-content: center;
  gap: 20px;
}
div h1 {
  color: var(--brand-blue);
  font-weight: bolder;
  font-size: 40px;
  margin: 0;
}
div h1 span {
  color: var(--brand-green);
}
.reload {
  color: var(--brand-blue);
  font-size: 20px;
  margin-top: 50px;
}
</style>
