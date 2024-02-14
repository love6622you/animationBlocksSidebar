<template>
  <div class="mx-auto h-dvh max-w-screen-sm bg-gray-200">
    <header class="flex w-full justify-end bg-white p-4">
      <Burger />
    </header>

    <main class="grid h-[calc(100%-60px)] place-items-center">
      <!-- 九宮格 -->
      <div class="grid grid-cols-3 grid-rows-3 gap-1 overflow-hidden">
        <div
          v-for="i in 9"
          :key="i"
          class="box-gradient relative flex h-[100px] w-[100px] border-2 border-black"
        >
          <BallMask v-if="[3, 5, 9].includes(i)" />
          <Ball v-if="[1, 3, 7, 9].includes(i)" />
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import Burger from './components/Burger.vue';
import BallMask from './components/BallMask.vue';
import Ball from './components/Ball.vue';
</script>

<style scoped>
.box-gradient {
  background: radial-gradient(circle, rgba(113, 81, 95, 1) 81%, rgba(0, 0, 0, 1) 100%);
}
</style>
