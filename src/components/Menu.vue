<template>
  <ul>
    <li v-for="item in data" :key="item.key">
      <div :class="[{ 'text-yellow-400': openItems[item.key] }, 'p-2.5']" @click="toggle(item)">
        {{ item.text }}
      </div>
      <template v-if="item.children && openItems[item.key]">
        <Menu :data="item.children" />
      </template>
    </li>
  </ul>
</template>

<script setup>
import { reactive } from 'vue';

const props = defineProps({
  data: {
    type: Array,
    required: true,
  },
});

const openItems = reactive({});
const toggle = (item) => {
  openItems[item.key] = !openItems[item.key];
  closeOthers(item);
};

const closeOthers = (currentItem) => {
  Object.keys(openItems).forEach((key) => {
    if (key !== currentItem.key) {
      openItems[key] = false;
    }
  });
};
</script>

<style scoped>
ul ul {
  padding-left: 20px;
}

ul > li:has(ul) {
  background: grey;
}
</style>
