<template>
  <div class="movements">
    <div class="content">
      <MoVement
        v-for="movement in movements"
        :key="movement.id"
        :title="movement.title"
      />
    </div>
  </div>
</template>

<script setup>
import MoVement from "./MoVement.vue";
import { defineProps, toRefs } from "vue";

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
.title {
  margin: 8px 16px 24px 16px;
  color: var(--brand-blue);
}
.content {
  max-height: 68vh;
  display: flex;
  flex-direction: column;
  gap: 8px;
  overflow-y: scroll;
}
</style>
