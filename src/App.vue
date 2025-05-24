<script setup>
import Header from './components/Header.vue'
import Sidebar from './components/Sidebar.vue'
</script>

<template>
  <Header />
  <div class="content-container">
    <Sidebar />
    <router-view />
  </div>
</template>

<style>
/* Global styles */
.content-container {
  display: flex;
  margin-top: 8vh;
  min-height: 92vh;
  width: 100%;
}

/* Responsive design */
@media (max-width: 1023px) {
  .content-container {
    flex-direction: column;
  }
}
</style>