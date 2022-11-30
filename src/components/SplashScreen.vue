<template>
  <div class="splashscreen">
    <img src="@/assets/paisaje-azul.svg" alt="logo" />
    <h1 class=""><span>Splas</span>Screen</h1>
    <div>
      <p>Cargando ...</p>
    </div>
  </div>
</template>

<style>
.splashscreen {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
h1 {
  color: var(--brand-green);
}
h1 span {
  color: var(--brand-blue);
}
.splashscreen div {
  position: relative;
  top: 40px;
}
.splashscreen div p {
  color: var(--brand-blue);
}
</style>
