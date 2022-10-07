<script setup lang="ts">
import SplashScreen from "./components/SplashScreen.vue";
import { defineAsyncComponent, Suspense } from "vue";
import Home from "./components/Home.vue";
const asyncComp = defineAsyncComponent(() => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(Home)
    }, 2500)
  })
})
</script>

<template>
  <Suspense>
    <template #default>
      <asyncComp />
    </template>
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

<style scoped>

</style>
