<template>
  <div class="product-card" :class="{ 'out-of-stock': !product.availability }">
    <div class="card-image-placeholder">
      <span class="card-category-tag">{{ product.category }}</span>
      <span class="card-commune-badge">{{ product.commune }}</span>
    </div>
    
    <div class="card-content">
      <h3 class="card-title">{{ product.name }}</h3>
      
      <div class="card-info">
        <p class="info-item">
          <span class="info-label">Productor:</span> 
          <span class="info-value">{{ product.producer }}</span>
        </p>
        <p class="info-item">
          <span class="info-label">Comuna:</span> 
          <span class="info-value font-highlight">{{ product.commune }}</span>
        </p>
      </div>

      <div class="card-footer">
        <div class="card-price">
          <span class="price-symbol">$</span>
          <span class="price-val">{{ formatPrice(product.price) }}</span>
        </div>
        
        <div class="card-stock" :class="product.availability ? 'in-stock' : 'no-stock'">
          {{ product.availability ? 'Disponible' : 'Sin Stock' }}
        </div>
      </div>

      <button 
        class="action-btn"
        :class="{ 'is-interested': isInterested }"
        @click="$emit('toggle-interest', product)"
      >
        <span class="btn-text">{{ isInterested ? 'Interesado' : 'Me interesa' }}</span>
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  product: {
    type: Object,
    required: true
  },
  isInterested: {
    type: Boolean,
    default: false
  }
})

defineEmits(['toggle-interest'])

const formatPrice = (value) => {
  if (value === undefined || value === null) return '0'
  return value.toLocaleString('es-CL')
}
</script>

<style scoped>
.product-card {
  background: var(--color-surface);
  border: 1px solid var(--border-color);
  border-radius: 8px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  height: 100%;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

.product-card:hover {
  border-color: var(--color-primary);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.product-card.out-of-stock {
  opacity: 0.7;
}

.card-image-placeholder {
  background-color: var(--color-surface-hover);
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  border-bottom: 1px solid var(--border-color);
}

.card-category-tag {
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  color: var(--color-primary);
  letter-spacing: 0.5px;
}

.card-commune-badge {
  position: absolute;
  bottom: 8px;
  left: 8px;
  background-color: var(--color-accent);
  color: #ffffff;
  padding: 0.2rem 0.5rem;
  border-radius: 4px;
  font-size: 0.7rem;
  font-weight: 600;
}

.card-content {
  padding: 1rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.card-title {
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 0.8rem;
  color: var(--text-primary);
  line-height: 1.3;
}

.card-info {
  margin-bottom: 1rem;
  flex-grow: 1;
}

.info-item {
  font-size: 0.85rem;
  margin-bottom: 0.25rem;
  display: flex;
  justify-content: space-between;
}

.info-label {
  color: var(--text-secondary);
}

.info-value {
  color: var(--text-primary);
  font-weight: 500;
}

.font-highlight {
  color: var(--color-primary);
}

.card-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.8rem;
  padding-top: 0.6rem;
  border-top: 1px solid var(--border-color);
}

.card-price {
  color: var(--text-primary);
  font-weight: 700;
  font-size: 1.15rem;
}

.price-symbol {
  font-size: 0.85rem;
  color: var(--color-primary);
  margin-right: 1px;
}

.card-stock {
  font-size: 0.7rem;
  font-weight: 700;
  padding: 0.15rem 0.4rem;
  border-radius: 4px;
}

.in-stock {
  background-color: rgba(30, 126, 52, 0.1);
  color: var(--color-primary);
}

.no-stock {
  background-color: rgba(220, 53, 69, 0.1);
  color: #dc3545;
}

.action-btn {
  background-color: transparent;
  border: 1px solid var(--border-color);
  color: var(--text-primary);
  padding: 0.5rem;
  border-radius: 4px;
  font-family: inherit;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
}

.action-btn:hover {
  background-color: var(--color-surface-hover);
  border-color: var(--text-secondary);
}

.action-btn.is-interested {
  background-color: var(--color-primary);
  border-color: var(--color-primary);
  color: #ffffff;
}

.action-btn.is-interested:hover {
  background-color: var(--color-primary-hover);
}
</style>
