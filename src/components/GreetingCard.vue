<script setup lang="ts">
defineProps<{
  greeting: string;
}>();
</script>

<template>
  <div class="greeting-card">
    <div class="card-header">
      <span class="card-flower left">🌷</span>
      <h1>С 8 Марта!</h1>
      <span class="card-flower right">🌷</span>
    </div>
    <div class="card-divider"></div>
    <p class="greeting-text">{{ greeting }}</p>
    <div class="card-divider"></div>
  </div>
</template>

<style scoped>
.greeting-card {
  background: linear-gradient(160deg, #fff8f0, #fff0f5, #fce4ec);
  border: 2px solid #f0c0d0;
  border-radius: 16px;
  padding: 2.5rem 2rem;
  box-shadow: 0 12px 48px rgba(200, 100, 130, 0.2);
  text-align: center;
}

.card-header {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  margin-bottom: 1rem;
}

.card-header h1 {
  font-size: 2.2rem;
  color: #c2185b;
  margin: 0;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.06);
}

.card-flower {
  font-size: 2rem;
  animation: sway 2s ease-in-out infinite alternate;
}

.card-flower.right {
  animation-delay: 0.5s;
}

@keyframes sway {
  from {
    transform: rotate(-8deg);
  }
  to {
    transform: rotate(8deg);
  }
}

.card-divider {
  height: 2px;
  background: linear-gradient(90deg, transparent, #f0a0c0, transparent);
  margin: 1rem auto;
  width: 80%;
  border-radius: 2px;
}

.greeting-text {
  font-size: 1.2rem;
  line-height: 1.7;
  color: #5d3a4a;
  padding: 0.5rem 1rem;
  font-style: italic;
}

@media (max-width: 480px) {
  .card-header h1 {
    font-size: 1.6rem;
  }
  .greeting-text {
    font-size: 1rem;
  }
}
</style>
