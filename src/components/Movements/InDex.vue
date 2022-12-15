<template>
  <div class="movements">
    <div class="content">
      <MoVement
        v-for="movement in movements"
        :key="movement.id"
        :title="movement.title"
        :descripcion="movement.description"
        :identificador="movement.id"
        :moneyAmount="movement.amount"
        @remove="seeRemove"
      />
    </div>
  </div>
</template>

<script setup>
import MoVement from "./MoVement.vue";
import { defineProps, toRefs, defineEmits } from "vue";

const emit = defineEmits(["eliminar"]);
const seeRemove = (e) => {
  emit("eliminar", e);
};

const props = defineProps({
  movements: {
    type: Array,
    default: () => [],
  },
});

const { movements } = toRefs(props);
</script>

<style scoped>
.movements {
  max-height: 100%;
  padding: 0 8px;
  margin-bottom: 14px;
}

.content {
  max-height: 68vh;
  display: flex;
  flex-direction: column;
  gap: 8px;
  overflow-y: scroll;
}
</style>
