<template>
  <div class="productos-container">
    <h1>Catálogo de Productos - Mercado Ñuble Digital</h1>
    <div class="grid-productos">
      <ProductCard
        v-for="producto in productos"
        :key="producto.id"
        :nombre="producto.nombre"
        :categoria="producto.categoria"
        :productor="producto.productor"
        :comuna="producto.comuna"
        :precio="producto.precio"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ProductCard from '../components/ProductCard.vue'

const productos = ref([
  {
    id: 1,
    nombre: 'Miel Multifloral Orgánica',
    categoria: 'Conservas y Miel',
    productor: 'Apícola San Carlos',
    comuna: 'San Carlos',
    precio: 6500
  },
  {
    id: 2,
    nombre: 'Queso Mantecoso Artesanal',
    categoria: 'Lácteos',
    productor: 'Lácteos Quirihue',
    comuna: 'Quirihue',
    precio: 8000
  },
  {
    id: 3,
    nombre: 'Mermelada de Maqui',
    categoria: 'Conservas y Miel',
    productor: 'Sabores del Carmen',
    comuna: 'El Carmen',
    precio: 3500
  },
  {
    id: 4,
    nombre: 'Greda Tradicional Quinchamalí',
    categoria: 'Artesanía',
    productor: 'Alfarería Rosa',
    comuna: 'Chillán',
    precio: 12000
  },
  {
    id: 5,
    nombre: 'Longaniza Tradicional',
    categoria: 'Embutidos',
    productor: 'Chacinería San Carlos',
    comuna: 'San Carlos',
    precio: 7500
  },
  {
    id: 6,
    nombre: 'Castañas en Almíbar',
    categoria: 'Conservas y Miel',
    productor: 'Frutos de Coihueco',
    comuna: 'Coihueco',
    precio: 4500
  }
])
</script>

<style scoped>
.productos-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.grid-productos {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
  margin-top: 1.5rem;
}
</style>