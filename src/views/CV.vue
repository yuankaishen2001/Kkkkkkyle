<template>
  <div class="cv-container">
    <iframe
      :src="cvUrl"
      width="100%"
      height="100%"
      frameborder="0"
    ></iframe>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const cvUrl = ref('/src/assets/profile/CV.pdf')
</script>

<style scoped>
.cv-container {
  width: 100%;
  height: 100vh;
  overflow: hidden;
}
</style> 