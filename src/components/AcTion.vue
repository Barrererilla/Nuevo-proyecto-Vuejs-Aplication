<template>
  <div>
    <button @click="showModal = true">Agregar movimiento</button>
    <teleport to="#app">
      <MoDal v-if="showModal" @close="showModal = false">
        <ForMulario @submit="showModal = false" />
      </MoDal>
    </teleport>
  </div>
</template>

<script setup>
import { ref, defineExpose } from "vue";
import MoDal from "./showModal/MoDal.vue";
import ForMulario from "./showModal/ForMulario.vue";

const showModal = ref(false);

defineExpose({
  showModal,
});
</script>

<style scoped>
button {
  color: white;
  font-size: 1.25rem;
  background-color: var(--brand-blue);
  border: none;
  width: 100%;
  padding: 24px 60px;
  border-radius: 60px;
  box-sizing: border-box;
}
</style>
