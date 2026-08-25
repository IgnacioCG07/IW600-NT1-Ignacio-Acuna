<template>
  <div class="productos-container">
    <h1 class="section-title">Catálogo de Productos</h1>
    <p class="section-description">Explora los productos locales disponibles en las comunas de la Región de Ñuble.</p>
    <div class="placeholder-content">
      <p>Cargando el catálogo de productores locales...</p>
    </div>
  </div>
</template>

<script setup>
// Lógica temporal para la Parte A
</script>

<style scoped>
.productos-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem;
}
.section-title {
  font-size: 2.2rem;
  color: var(--color-primary, #2ecc71);
  margin-bottom: 0.5rem;
}
.section-description {
  color: var(--text-secondary, #bdc3c7);
  margin-bottom: 2rem;
}
.placeholder-content {
  text-align: center;
  padding: 3rem;
  background: rgba(255, 255, 255, 0.02);
  border-radius: 8px;
  border: 1px dashed rgba(255, 255, 255, 0.1);
  color: var(--text-secondary, #bdc3c7);
}
</style>
