<script setup lang="ts">
import { ref } from "vue";
import { getRandomGreeting } from "./data/greetings";
import logoSrc from "./assets/logo_gkzn.png";
import FloatingPetals from "./components/FloatingPetals.vue";
import EnvelopeCard from "./components/EnvelopeCard.vue";
import GreetingCard from "./components/GreetingCard.vue";
import VideoSection from "./components/VideoSection.vue";

const VIDEO_URL = "/assets/video/поздравление.mp4";

const opened = ref(false);
const greeting = ref("");

function handleOpen() {
  greeting.value = getRandomGreeting();
  opened.value = true;
}
</script>

<template>
  <div class="page">
    <FloatingPetals />

    <div class="logo-container">
      <img :src="logoSrc" alt="Логотип организации" class="org-logo" />
    </div>

    <EnvelopeCard v-if="!opened" @open="handleOpen" />

    <transition name="fade-up">
      <div v-if="opened" class="card-container">
        <GreetingCard :greeting="greeting" />
        <VideoSection :video-url="VIDEO_URL" />
      </div>
    </transition>
  </div>
</template>

<style scoped>
.page {
  position: relative;
  min-height: 100vh;
  overflow-x: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  padding: 1rem;
}

.logo-container {
  position: fixed;
  top: 16px;
  left: 16px;
  z-index: 100;
}

.org-logo {
  height: 64px;
  width: auto;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
  background: white;
  padding: 4px;
}

.card-container {
  z-index: 1;
  max-width: 640px;
  width: 100%;
  margin-top: 100px;
  padding-bottom: 3rem;
}

.fade-up-enter-active {
  transition: all 0.8s cubic-bezier(0.22, 1, 0.36, 1);
}

.fade-up-enter-from {
  opacity: 0;
  transform: translateY(40px);
}

@media (max-width: 480px) {
  .org-logo {
    height: 44px;
  }
  .card-container {
    margin-top: 80px;
  }
}
</style>
