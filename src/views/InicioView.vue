<template>
  <div class="inicio-container">
    <div class="hero-section">
      <h1 class="main-title">Mercado Ñuble Digital</h1>
      <p class="subtitle">Conectando el trabajo de nuestros productores locales de la Región de Ñuble con la comunidad.</p>
    </div>
    
    <div class="info-grid">
      <div class="info-card">
        <h3>Productos de Calidad</h3>
        <p>Desde la miel pura de San Carlos hasta las hortalizas frescas de Coihueco, encuentra lo mejor de nuestra tierra.</p>
      </div>
      <div class="info-card">
        <h3>Directo del Productor</h3>
        <p>Identifica quién elabora cada artículo y conoce la comuna de origen para valorar el esfuerzo local.</p>
      </div>
      <div class="info-card">
        <h3>Manifiesta tu Interés</h3>
        <p>¿Te interesa algún producto del catálogo? Agrégalo a tu lista de interés para coordinar el contacto.</p>
      </div>
    </div>
  </div>
</template>

<script setup>
// Lógica de InicioView
</script>

<style scoped>
.inicio-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem;
}
.hero-section {
  text-align: center;
  margin-bottom: 3rem;
  padding: 3rem 1.5rem;
  background-color: var(--color-surface);
  border: 1px solid var(--border-color);
  border-radius: 8px;
}
.main-title {
  font-size: 2.5rem;
  color: var(--color-primary);
  margin-bottom: 1rem;
  font-weight: 700;
}
.subtitle {
  font-size: 1.15rem;
  color: var(--text-secondary);
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.6;
}
.info-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}
.info-card {
  background-color: var(--color-surface);
  padding: 2rem;
  border-radius: 8px;
  border: 1px solid var(--border-color);
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}
.info-card:hover {
  border-color: var(--color-primary);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}
.info-card h3 {
  font-size: 1.3rem;
  margin-bottom: 1rem;
  color: var(--color-primary);
}
.info-card p {
  color: var(--text-secondary);
  line-height: 1.5;
  font-size: 0.95rem;
}
</style>
