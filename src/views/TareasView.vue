<script setup>
import Tareas from '../components/Tareas.vue'
</script>

<template>
  <div class="view-container">
    <div class="view-header">
      <h1>Actividad N° 5 — Condicionales y Listas Dinámicas</h1>
      <p class="view-subtitle">
        Uso de <code>v-if</code>, <code>v-else</code>, <code>v-show</code> y <code>v-for</code> en Vue.js
      </p>
    </div>

    <Tareas />
  </div>
</template>

<style scoped>
.view-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.view-header {
  margin-bottom: 2rem;
}

.view-header h1 {
  font-size: 1.6rem;
  font-weight: 800;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.view-subtitle {
  color: var(--text-secondary);
  font-size: 0.95rem;
}

.view-subtitle code {
  background: rgba(30, 126, 52, 0.1);
  color: var(--color-primary);
  padding: 0.1rem 0.35rem;
  border-radius: 4px;
  font-size: 0.88rem;
  font-family: 'Courier New', monospace;
}
</style>
