<template>
  <div>
    <button @click="showModal = !showModal">Agregar movimiento</button>
    <teleport to="#app">
      <MoDal v-if="showModal" @close="showModal = !showModal">
        <form @submit.prevent="submit">
          <div class="field">
            <label>Title</label>
            <input type="text" v-model="title" />
          </div>
          <div class="field">
            <label for="">Amount</label>
            <input type="number" v-model="amount" />
          </div>
          <div class="field">
            <label for="">Description</label>
            <textarea rows="4" v-model="description"></textarea>
          </div>
          <div class="field">
            <label for="">Movement type</label>
            <label class="radio-label">
              <input type="radio" v-model="movementType" value="Ingreso" />
              <span>Ingreso</span>
            </label>
            <label class="radio-label">
              <input type="radio" v-model="movementType" value="Gasto" />
              <span>Gasto</span>
            </label>
          </div>
          <div class="action">
            <button>Add motion</button>
          </div>
        </form>
      </MoDal>
    </teleport>
  </div>
</template>

<script setup>
import { ref, defineEmits } from "vue";
import MoDal from "./showModal/MoDal.vue";

const title = ref("");
const amount = ref(0);
const description = ref("");
const movementType = ref("Ingreso");

const emit = defineEmits(["anadir"]);
const submit = () => {
  showModal.value = !showModal.value;
  emit("anadir", {
    id: new Date().getTime(),
    title: title.value,
    description: description.value,
    amount: movementType.value === "Gasto" ? -amount.value : amount.value,
    time: new Date(),
  });
  limpiar();
};

function limpiar() {
  title.value = "";
  description.value = "";
  amount.value = 0;
  movementType.value = "Ingreso";
}

const showModal = ref(false);
</script>

<style scoped>
button {
  color: white;
  font-size: 1.25rem;
  background-color: var(--brand-blue);
  border: none;
  width: 100%;
  height: 40px;
  padding: 24px 60px;
  border-radius: 60px;
  box-sizing: border-box;
  line-height: 5px;
}
form {
  font-size: 1.24rem;
  width: 100%;
}
form .action {
  padding: 0 24px;
}
.field {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  padding: 16px 24px;
}
label {
  margin-bottom: 8px;
}
input,
textarea {
  font-size: 1.24rem;
  border: 2px solid var(--brand-blue);
  border-radius: 8px;
  padding: 8px;
}
input[type="number"] {
  text-align: right;
}
.radio-label {
  display: flex;
  align-items: center;
  margin-top: 8px;
}
.radio-label span {
  margin-top: 4px;
  margin-left: 8px;
}
input[type="radio"] {
  appearance: none;
  width: 1.24rem;
  height: 1.24rem;
  color: var(--brand-blue);
  border: 2px solid var(--brand-blue);
  border-radius: 50%;
}
input[type="radio"]:checked {
  background-color: var(--brand-blue);
}
</style>
