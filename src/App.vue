<script setup>
/* import Home from "./components/Home.vue"; */
import { defineAsyncComponent } from "vue";
import SplashScreen from "./components/SplashScreen.vue";

const Home = defineAsyncComponent(() => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(import("./components/Home.vue"));
    }, 2000);
  });
});
</script>

<template>
  <Suspense>
    <Home />
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

<style>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
