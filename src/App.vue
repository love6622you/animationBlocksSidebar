<template>
  <div class="mx-auto h-dvh max-w-screen-sm bg-gray-200">
    <main class="grid h-full place-items-center">
      <!-- 九宮格 -->
      <div class="grid grid-cols-3 grid-rows-3 gap-1">
        <!-- v-for 建立9個 block -->
        <div
          v-for="i in 9"
          :key="i"
          class="block-gradient relative flex h-[100px] w-[100px] border-2 border-black"
        >
          <div v-if="[3, 5, 9].includes(i)" class="mask" />
          {{ i }}
        </div>
      </div>
    </main>
  </div>
</template>

<script setup></script>

<style scoped>
.block-gradient {
  background: radial-gradient(circle, rgba(113, 81, 95, 1) 81%, rgba(0, 0, 0, 1) 100%);
}

.mask {
  @apply absolute inset-0 h-full w-full animate-blink bg-white bg-opacity-40;
}
</style>
