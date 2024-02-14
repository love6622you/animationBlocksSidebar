<template>
  <div>
    <input id="menu" v-model="open" type="checkbox" class="hidden" />
    <label for="menu" class="space-y-2">
      <span class="block h-1 w-6 bg-black"></span>
      <span class="block h-1 w-6 bg-black"></span>
      <span class="block h-1 w-6 bg-black"></span>
    </label>
  </div>

  <Sidebar :open="open" @close="close" />
</template>

<script setup>
import Sidebar from './Sidebar.vue';
import { ref } from 'vue';

const open = ref(false);
const close = () => {
  open.value = false;
};
</script>

<style scoped></style>
