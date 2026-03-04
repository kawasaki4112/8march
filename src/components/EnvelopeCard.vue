<script setup lang="ts">
import { ref, onMounted } from "vue";

defineEmits<{
  open: [];
}>();

const ready = ref(false);

onMounted(() => {
  setTimeout(() => {
    ready.value = true;
  }, 100);
});
</script>

<template>
  <div class="envelope-scene">
    <div
      class="envelope-wrapper"
      :class="{ 'fly-in': ready }"
      @click="$emit('open')"
    >
      <div class="envelope">
        <div class="envelope-body">
          <div class="envelope-flap"></div>
          <div class="envelope-front">
            <span class="envelope-label">💌</span>
            <p class="envelope-hint">Нажмите, чтобы открыть</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.envelope-scene {
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 1;
  min-height: 70vh;
  z-index: 1;
}

.envelope-wrapper {
  cursor: pointer;
  transform: translateX(-120vw) rotate(-30deg);
  opacity: 0;
  transition:
    transform 1.4s cubic-bezier(0.22, 1, 0.36, 1),
    opacity 0.8s ease;
}

.envelope-wrapper.fly-in {
  transform: translateX(0) rotate(0deg);
  opacity: 1;
}

.envelope-wrapper:hover {
  transform: scale(1.08);
}

.envelope {
  width: 220px;
  height: 160px;
  position: relative;
}

.envelope-body {
  width: 100%;
  height: 100%;
  position: relative;
}

.envelope-front {
  width: 100%;
  height: 100%;
  background: linear-gradient(145deg, #fff5f5, #ffe0e6);
  border: 2px solid #e8a0b0;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: 0 8px 32px rgba(200, 100, 120, 0.25);
  position: relative;
  z-index: 2;
}

.envelope-flap {
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  height: 50%;
  background: linear-gradient(160deg, #ffd6df, #ffb6c8);
  border: 2px solid #e8a0b0;
  border-radius: 8px 8px 0 0;
  clip-path: polygon(0 0, 100% 0, 50% 100%);
  z-index: 3;
}

.envelope-label {
  font-size: 56px;
  margin-bottom: 4px;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.1));
}

.envelope-hint {
  font-size: 13px;
  color: #b06070;
  margin: 0;
  font-style: italic;
}

@media (max-width: 480px) {
  .envelope {
    width: 180px;
    height: 130px;
  }
  .envelope-label {
    font-size: 42px;
  }
}
</style>
