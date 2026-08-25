<template>
  <div class="product-card">
    <div class="info">
      <h3>{{ nombre }}</h3>
      <span class="categoria">{{ categoria }}</span>
      <p><strong>Productor:</strong> {{ productor }}</p>
      <p><strong>Comuna:</strong> {{ comuna }}</p>
      <p class="precio"><strong>Precio:</strong> ${{ precio.toLocaleString('es-CL') }}</p>
    </div>

    <!-- Botón que emite el evento al padre -->
    <button class="btn-interes" @click="emitirInteres">
       Me interesa
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  id: {
    type: Number,
    required: true
  },
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

// Declaramos el evento 'interes'
const emit = defineEmits(['interes'])

const emitirInteres = () => {
  // Emitimos el evento enviando los datos del producto
  emit('interes', { id: props.id, nombre: props.nombre })
}
</script>

<style scoped>
.product-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 1rem;
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
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

.btn-interes {
  margin-top: 1rem;
  padding: 0.6rem 1rem;
  background-color: #2e7d32;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.2s;
}

.btn-interes:hover {
  background-color: #1b5e20;
}
</style>