<template>
  <div>
    <div v-if="open" class="fixed inset-0 z-50 h-full w-screen" @click="emit('close')"></div>
    <transition name="slide">
      <div
        v-if="open"
        class="fixed right-0 top-0 z-50 h-full w-[250px] overflow-y-auto bg-black/90 p-4 text-white"
      >
        <Menu :data="menuList" />
      </div>
    </transition>
  </div>
</template>

<script setup>
import Menu from './Menu.vue';
import menuList from '../constants/menuList.json';

const props = defineProps({
  open: Boolean,
});

const emit = defineEmits(['close']);
</script>

<style scoped></style>
