<template>
  <div id="app">
    <BasicLayout />
  </div>
</template>

<script setup lang="ts">
import BasicLayout from "@/layouts/BasicLayout.vue";
import { onMounted } from 'vue'
const welcomeLog = () => {
  console.log("欢迎使用lei-picture-frontend！")
}
onMounted(() => {
  welcomeLog()
})
</script>

<style>
#app {
}
</style>
