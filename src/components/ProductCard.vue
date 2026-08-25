<template>
  <div class="product-card">
    <h3>{{ nombre }}</h3>
    <span class="categoria">{{ categoria }}</span>
    <p><strong>Productor:</strong> {{ productor }}</p>
    <p><strong>Comuna:</strong> {{ comuna }}</p>
    <p class="precio"><strong>Precio:</strong> ${{ precio.toLocaleString('es-CL') }}</p>
  </div>
</template>

<script setup>
defineProps({
  nombre: {
    type: String,
    required: true
  },
  categoria: {
    type: String,
    required: true
  },
  productor: {
    type: String,
    required: true
  },
  comuna: {
    type: String,
    required: true
  },
  precio: {
    type: Number,
    required: true
  }
})
</script>

<style scoped>
.product-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 1rem;
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.categoria {
  display: inline-block;
  background-color: #e8f5e9;
  color: #2e7d32;
  font-size: 0.85rem;
  padding: 0.25rem 0.5rem;
  border-radius: 4px;
  margin-bottom: 0.5rem;
}

.precio {
  font-size: 1.1rem;
  color: #d32f2f;
}
</style>