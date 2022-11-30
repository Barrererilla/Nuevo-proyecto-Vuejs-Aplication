<template>
  <Suspense>
    <template #fallback>
      <SplashScreen />
    </template>
    <template #default>
      <HoMe />
    </template>
  </Suspense>
</template>

<script>
import { defineAsyncComponent } from "vue";
import SplashScreen from "./components/SplashScreen.vue";

export default {
  components: {
    SplashScreen,
    HoMe: defineAsyncComponent(() => {
      return new Promise((resol) => {
        setTimeout(() => {
          resol(import("./components/HoMe.vue"));
        }, 2500);
      });
    }),
  },
};
</script>

<style>
html,
body,
.app {
  font-family: Arial, Helvetica, sans-serif;
  margin: 0;
  min-height: 100vh;
}

* {
  --brand-green: rgb(31, 185, 31);
  --brand-blue: rgb(16, 189, 198);
}
</style>
