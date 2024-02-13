<template>
  <div
    ref="ballRef"
    :class="[
      'absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2',
      'grid place-items-center',
      'h-[1.875rem] w-[1.875rem]',
      'rounded-full bg-[#A5F12B]',
      'z-10',
    ]"
  >
    0
  </div>
</template>

<script setup>
const DURATION = 2000;

import { ref, onMounted, onBeforeUnmount } from 'vue';

const ballRef = ref(null);
const easeInOutQuad = (t) => (t < 0.5 ? 2 * t * t : -1 + (4 - 2 * t) * t);

const animate = () => {
  let start = null;
  const step = (timestamp) => {
    if (!start) start = timestamp;
    const progress = timestamp - start;

    const easedProgress = easeInOutQuad(Math.min(progress / DURATION, 1));

    ballRef.value.style.transform = `translateX(${easedProgress * 200}px) translateY(-50%)`;

    if (progress < DURATION) {
      requestAnimationFrame(step);
    } else {
      start = null;
      ballRef.value.style.transform = 'translateX(0) translateY(-50%)';
      requestAnimationFrame(step);
    }
  };

  requestAnimationFrame(step);
};

onMounted(() => {
  // 啟動動畫
  requestAnimationFrame(animate);
});

onBeforeUnmount(() => {
  // 取消動畫
  cancelAnimationFrame(animate);
});
</script>

<style scoped></style>
