<template>
  <div class="mask"></div>
</template>

<script setup></script>

<style scoped>
.mask {
  @apply absolute inset-0 h-full w-full animate-blink bg-white bg-opacity-40;
}
</style>
