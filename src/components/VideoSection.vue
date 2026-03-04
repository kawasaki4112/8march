<script setup lang="ts">
defineProps<{
  videoUrl: string;
}>();
</script>

<template>
  <div class="video-section">
    <h2>Видеопоздравление</h2>
    <video controls :src="videoUrl" class="video-player" preload="metadata">
      Ваш браузер не поддерживает воспроизведение видео.
    </video>
    <a
      :href="videoUrl"
      download="Поздравление_с_8_Марта.mp4"
      class="download-btn"
    >
      ⬇ Скачать видеопоздравление
    </a>
  </div>
</template>

<style scoped>
.video-section {
  margin-top: 2rem;
  text-align: center;
}

.video-section h2 {
  color: #c2185b;
  margin-bottom: 1rem;
  font-size: 1.4rem;
}

.video-player {
  width: 100%;
  max-width: 640px;
  border-radius: 12px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15);
  background: #000;
}

.download-btn {
  display: inline-block;
  margin-top: 1.2rem;
  padding: 0.8rem 2rem;
  background: linear-gradient(135deg, #e91e63, #c2185b);
  color: #fff;
  text-decoration: none;
  border-radius: 30px;
  font-size: 1rem;
  font-weight: 600;
  box-shadow: 0 4px 16px rgba(233, 30, 99, 0.35);
  transition:
    transform 0.2s,
    box-shadow 0.2s;
}

.download-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 24px rgba(233, 30, 99, 0.45);
  color: #fff;
}
</style>
