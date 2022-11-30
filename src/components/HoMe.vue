<template>
  <LayOut>
    <template #head>
      <HeaDer />
    </template>
  </LayOut>
</template>

<script>
import HeaDer from "./HeaDer.vue";
import LayOut from "./LayOut.vue";

export default {
  components: {
    HeaDer,
    LayOut,
  },
};
</script>
