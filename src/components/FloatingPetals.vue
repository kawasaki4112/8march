<script setup lang="ts">
const petals = Array.from({ length: 20 }, () => ({
  left: Math.random() * 100 + "%",
  animationDelay: Math.random() * 8 + "s",
  animationDuration: 6 + Math.random() * 6 + "s",
  fontSize: 12 + Math.random() * 18 + "px",
  opacity: 0.4 + Math.random() * 0.5,
}));
</script>

<template>
  <div class="petals">
    <div v-for="(style, i) in petals" :key="i" class="petal" :style="style">
      🌸
    </div>
  </div>
</template>

<style scoped>
.petals {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 0;
  overflow: hidden;
}

.petal {
  position: absolute;
  top: -30px;
  animation: fall linear infinite;
}

@keyframes fall {
  0% {
    transform: translateY(-10vh) translateX(0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    transform: translateY(110vh) translateX(40px) rotate(360deg);
    opacity: 0;
  }
}
</style>
