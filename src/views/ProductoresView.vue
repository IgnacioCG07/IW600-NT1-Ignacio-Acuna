<template>
  <div class="productores-container">
    <h1 class="section-title">Nuestros Productores</h1>
    <p class="section-description">Conoce a las personas y familias detrás de los productos artesanales e industriales de Ñuble.</p>
    <div class="placeholder-content">
      <p>Cargando información sobre los productores locales de la región...</p>
    </div>
  </div>
</template>

<script setup>
// Lógica temporal para la Parte A
</script>

<style scoped>
.productores-container {
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
