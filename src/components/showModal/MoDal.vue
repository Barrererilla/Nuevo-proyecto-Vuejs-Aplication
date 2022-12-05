<template>
  <div class="modal-body">
    <div class="header-modal">
      <p>Nuevo movimiento</p>
      <img src="@/assets/icon-equis.svg" alt="Cerrar" @click="close" />
    </div>
    <div class="header">
      <slot></slot>
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from "vue";

const emit = defineEmits(["close"]);

const close = () => {
  emit("close");
};
</script>

<style scoped>
.modal-body {
  z-index: 2;
  position: absolute;
  bottom: 0;
  top: 0;
  right: 0;
  left: 0;
  background-color: white;
}
.header-modal {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 14px 14px;
  width: 100%;
}
p {
  margin: 0;
  font-size: 25px;
  color: var(--brand-blue);
}
</style>
