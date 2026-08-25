<template>
  <div class="app-layout">
    <header class="app-header">
      <div class="header-container">
        <router-link to="/" class="logo-link">
          <div class="logo">
            <span class="logo-text">Mercado Ñuble Digital</span>
          </div>
        </router-link>
        
        <nav class="nav-menu">
          <router-link to="/" class="nav-link" active-class="active-link">Inicio</router-link>
          <router-link to="/productos" class="nav-link" active-class="active-link">Productos</router-link>
          <router-link to="/productores" class="nav-link" active-class="active-link">Productores</router-link>
          <router-link to="/contacto" class="nav-link" active-class="active-link">Contacto</router-link>
        </nav>

        <div class="header-actions">
          <div class="interest-badge" title="Productos de interés">
            <span class="badge-label">Interés:</span>
            <span class="badge-count">{{ interestCount }}</span>
          </div>
        </div>
      </div>
    </header>

    <main class="app-main">
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component 
            :is="Component" 
            :interests="interests" 
            @toggle-interest="handleToggleInterest" 
          />
        </transition>
      </router-view>
    </main>

    <footer class="app-footer">
      <div class="footer-container">
        <p>&copy; 2026 Mercado Ñuble Digital - Prototipo Frontend para la Región de Ñuble.</p>
        <p class="footer-sub">Desarrollado con Vue 3 y Vue Router.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed, provide } from 'vue'

// State for user's interested products
const interests = ref([])

const interestCount = computed(() => interests.value.length)

const handleToggleInterest = (product) => {
  const index = interests.value.findIndex(p => p.id === product.id)
  if (index === -1) {
    interests.value.push(product)
  } else {
    interests.value.splice(index, 1)
  }
}

provide('interests', interests)
provide('toggleInterest', handleToggleInterest)
</script>

<style>
/* Global CSS variables - Simple clean flat styling */
:root {
  --color-bg: #f8f9fa;
  --color-surface: #ffffff;
  --color-surface-hover: #f1f3f5;
  --color-primary: #1e7e34; /* Flat Forest Green */
  --color-primary-hover: #155d24;
  --color-accent: #495057;
  --text-primary: #212529;
  --text-secondary: #6c757d;
  --border-color: #dee2e6;
  --font-sans: 'Inter', system-ui, -apple-system, sans-serif;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: var(--color-bg);
  color: var(--text-primary);
  font-family: var(--font-sans);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  line-height: 1.5;
}

/* Base App Layout */
.app-layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.app-header {
  background-color: var(--color-surface);
  border-bottom: 1px solid var(--border-color);
  position: sticky;
  top: 0;
  z-index: 100;
  padding: 1rem 0;
}

.header-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo-link {
  text-decoration: none;
  color: inherit;
}

.logo {
  display: flex;
  align-items: center;
}

.logo-text {
  font-size: 1.4rem;
  font-weight: 750;
  color: var(--color-primary);
  letter-spacing: -0.5px;
}

.nav-menu {
  display: flex;
  gap: 1rem;
}

.nav-link {
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: 500;
  padding: 0.5rem 0.8rem;
  border-radius: 4px;
  transition: all 0.2s ease;
}

.nav-link:hover {
  color: var(--text-primary);
  background-color: var(--color-surface-hover);
}

.active-link {
  color: var(--color-primary);
  background-color: rgba(30, 126, 52, 0.08);
  font-weight: 600;
}

.interest-badge {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  background-color: var(--color-surface);
  border: 1px solid var(--border-color);
  padding: 0.4rem 0.8rem;
  border-radius: 4px;
  font-size: 0.9rem;
  font-weight: 600;
}

.badge-label {
  color: var(--text-secondary);
}

.badge-count {
  color: var(--color-primary);
  font-weight: 700;
}

.app-main {
  flex-grow: 1;
}

.app-footer {
  background-color: #f1f3f5;
  border-top: 1px solid var(--border-color);
  padding: 2rem 0;
  text-align: center;
  margin-top: 3rem;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.footer-container p {
  color: var(--text-secondary);
  font-size: 0.9rem;
}

.footer-sub {
  margin-top: 0.2rem;
  font-size: 0.8rem !important;
  opacity: 0.8;
}

/* Page transitions */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.15s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

@media (max-width: 768px) {
  .header-container {
    flex-direction: column;
    gap: 1rem;
  }
  
  .nav-menu {
    width: 100%;
    justify-content: center;
    gap: 0.25rem;
  }
  
  .nav-link {
    font-size: 0.85rem;
    padding: 0.4rem 0.6rem;
  }
  
  .interest-badge {
    margin-top: 0.2rem;
  }
}
</style>
