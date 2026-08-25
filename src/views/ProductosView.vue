<template>
  <div class="productos-container">
    <h1>Catálogo de Productos - Mercado Ñuble Digital</h1>

    <!-- Controles de filtrado -->
    <div class="filtro-container">
      <label for="comuna-select"><strong>Filtrar por comuna:</strong></label>
      <select id="comuna-select" v-model="comunaSeleccionada" class="select-comuna">
        <option value="todas">Todas las comunas</option>
        <option value="San Carlos">San Carlos</option>
        <option value="Quirihue">Quirihue</option>
        <option value="El Carmen">El Carmen</option>
        <option value="Chillán">Chillán</option>
        <option value="Coihueco">Coihueco</option>
        <option value="Bulnes">Bulnes</option> <!-- Opción sin productos para probar el v-else -->
      </select>
    </div>

    <!-- Lista dinámica de productos -->
    <div v-if="productosFiltrados.length > 0" class="grid-productos">
      <ProductCard
        v-for="producto in productosFiltrados"
        :key="producto.id"
        :nombre="producto.nombre"
        :categoria="producto.categoria"
        :productor="producto.productor"
        :comuna="producto.comuna"
        :precio="producto.precio"
      />
    </div>

    <!-- Mensaje cuando no hay productos que coincidan -->
    <div v-else class="mensaje-vacio">
      <p>No se encontraron productos disponibles para la comuna seleccionada.</p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import ProductCard from '../components/ProductCard.vue'

// Estado del filtro
const comunaSeleccionada = ref('todas')

// Arreglo de datos
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

// Propiedad computada para filtrar la lista según la comuna seleccionada
const productosFiltrados = computed(() => {
  if (comunaSeleccionada.value === 'todas') {
    return productos.value
  }
  return productos.value.filter(p => p.comuna === comunaSeleccionada.value)
})
</script>

<style scoped>
.productos-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.filtro-container {
  margin-bottom: 2rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.select-comuna {
  padding: 0.5rem 1rem;
  border-radius: 6px;
  border: 1px solid #ccc;
  font-size: 1rem;
}

.grid-productos {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}

.mensaje-vacio {
  padding: 2rem;
  background-color: #fff3cd;
  border: 1px solid #ffe399;
  color: #856404;
  border-radius: 8px;
  text-align: center;
  margin-top: 1.5rem;
}
</style>