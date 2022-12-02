<template>
  <div>
    <div class="header">
      <slot name="head"></slot>
    </div>
    <div class="resume">
      <slot name="resume"></slot>
    </div>
    <div class="movements">
      <div class="head" @click="showMovements = !showMovements">
        <div class="grip"></div>
      </div>
      <div class="historial">
        <h1 class="title-parent">Historial</h1>
      </div>
      <div class="body" v-if="showMovements">
        <slot name="movements"></slot>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const showMovements = ref(false);
</script>

<style scoped>
.header,
.movements,
.resume {
  display: flex;
  padding: 14px 20px;
  justify-content: space-around;
  align-items: center;
  box-sizing: border-box;
}
.header {
  position: fixed;
  width: 100vw;
}
.resume {
  min-height: 100vh;
}
.movements {
  z-index: 1;
  position: absolute;
  bottom: 0;
  box-shadow: 0 -8px 16px rgb(79, 233, 228);
  width: 100vw;
  flex-direction: column;
  border-radius: 24px;
  gap: 20px;
}
.movements .historial {
  width: 100vw;
  padding-left: 20px;
}
.movements .historial .title-parent {
  font-weight: bolder;
  color: rgb(52, 189, 239);
}
.movements .grip {
  width: 100px;
  height: 10px;
  background: rgb(173, 218, 239);
  border-radius: 14px;
}
.movements .body {
  width: 100vw;
  height: 75vh;
  background-color: white;
}
</style>
