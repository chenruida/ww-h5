<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <div class="layout">
    <RouterView />
  </div>
</template>

<style scoped>
.layout {
  background-image: url('./assets/images/back1.jpg');
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
  height: calc(100vh);
}
</style>
