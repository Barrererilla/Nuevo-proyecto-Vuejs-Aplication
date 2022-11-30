<template>
  <Suspense>
    <template>
      <HoMe />
    </template>
    <template #fallback>
      <SplashScreen />
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
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

* {
  --brand-green: rgb(46, 219, 46);
  --brand-blue: rgb(19, 106, 182);
}
</style>
