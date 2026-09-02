<script setup>
import { ref } from 'vue'

// --- Sección 1: Lista de Tareas ---
const nuevaTarea = ref('')
const tareas = ref([])
const mostrarTareas = ref(true)

function agregarTarea() {
  if (nuevaTarea.value.trim()) {
    tareas.value.push(nuevaTarea.value.trim())
    nuevaTarea.value = ''
  }
}

function eliminarTarea(index) {
  tareas.value.splice(index, 1)
}

// --- Sección 2: Lista de Personas ---
const mostrarPersonas = ref(true)
const list = ref([
  { nombre: 'Ana', apellido: 'Pérez' },
  { nombre: 'Luis', apellido: 'Gómez' },
  { nombre: 'María', apellido: 'Rodríguez' }
])

const nuevoNombre = ref('')
const nuevoApellido = ref('')

function agregarPersona() {
  const nombre = nuevoNombre.value.trim() || 'Nuevo'
  const apellido = nuevoApellido.value.trim() || 'Usuario'
  list.value.push({ nombre, apellido })
  nuevoNombre.value = ''
  nuevoApellido.value = ''
}

function eliminarPersona(index) {
  list.value.splice(index, 1)
}
</script>

<template>
  <div class="tareas-page">

    <!-- ===== SECCIÓN 1: TO-DO LIST ===== -->
    <section class="card">
      <div class="card-header">
        <h2>📝 Lista de Tareas</h2>
        <span class="badge">{{ tareas.length }} tarea{{ tareas.length !== 1 ? 's' : '' }}</span>
      </div>

      <!-- Input para agregar tarea -->
      <div class="input-row">
        <input
          v-model="nuevaTarea"
          @keyup.enter="agregarTarea"
          placeholder="Escribe una nueva tarea..."
          class="text-input"
        />
        <button @click="agregarTarea" class="btn btn-primary">Agregar</button>
        <button @click="mostrarTareas = !mostrarTareas" class="btn btn-secondary">
          {{ mostrarTareas ? '🙈 Ocultar' : '👁️ Mostrar' }} tareas
        </button>
      </div>

      <!-- Lista con v-show -->
      <ul v-show="mostrarTareas" class="task-list">
        <li
          v-for="(t, index) in tareas"
          :key="index"
          class="task-item"
        >
          <span class="task-index">{{ index + 1 }}.</span>
          <span class="task-text">{{ t }}</span>
          <button @click="eliminarTarea(index)" class="btn btn-danger btn-sm">✕</button>
        </li>
      </ul>

      <!-- Mensaje con v-if cuando lista vacía -->
      <p v-if="tareas.length === 0" class="empty-msg">
        📭 No hay tareas registradas. ¡Agrega una arriba!
      </p>

      <!-- Mensaje con v-else cuando lista oculta y tiene tareas -->
      <p v-else-if="!mostrarTareas" class="hidden-msg">
        🔒 La lista tiene {{ tareas.length }} tarea(s), pero está oculta.
      </p>
    </section>

    <!-- ===== SECCIÓN 2: LISTA DE PERSONAS ===== -->
    <section class="card">
      <div class="card-header">
        <h2>👥 Lista de Personas</h2>
        <span class="badge">{{ list.length }} persona{{ list.length !== 1 ? 's' : '' }}</span>
      </div>

      <!-- Inputs de nombre y apellido -->
      <div class="input-row persona-row">
        <input
          v-model="nuevoNombre"
          placeholder="Nombre"
          class="text-input"
        />
        <input
          v-model="nuevoApellido"
          placeholder="Apellido"
          class="text-input"
        />
        <button @click="agregarPersona" class="btn btn-primary">Agregar Persona</button>
        <button @click="mostrarPersonas = !mostrarPersonas" class="btn btn-secondary">
          {{ mostrarPersonas ? '🙈 Ocultar' : '👁️ Mostrar' }} Lista
        </button>
      </div>

      <!-- v-if: mostrar lista si visible Y tiene elementos -->
      <ul v-if="mostrarPersonas && list.length" class="task-list">
        <li
          v-for="(persona, index) in list"
          :key="index"
          class="task-item"
        >
          <span class="task-index">{{ index + 1 }}.</span>
          <span class="task-text">{{ persona.nombre }} {{ persona.apellido }}</span>
          <button @click="eliminarPersona(index)" class="btn btn-danger btn-sm">✕ Eliminar</button>
        </li>
      </ul>

      <!-- v-else-if: lista con datos pero oculta -->
      <p v-else-if="list.length" class="hidden-msg">
        🔒 La lista no está vacía, pero está oculta.
      </p>

      <!-- v-else: lista vacía -->
      <p v-else class="empty-msg">
        📭 La lista está vacía.
      </p>
    </section>

    <!-- ===== RESUMEN DE DIRECTIVAS ===== -->
    <section class="card info-card">
      <h2>📚 Directivas utilizadas en esta actividad</h2>
      <div class="directives-grid">
        <div class="directive-item">
          <code>v-model</code>
          <p>Vinculación bidireccional entre el input y la variable reactiva.</p>
        </div>
        <div class="directive-item">
          <code>v-for</code>
          <p>Renderiza cada elemento del arreglo como un ítem de la lista.</p>
        </div>
        <div class="directive-item">
          <code>v-if / v-else-if / v-else</code>
          <p>Muestra u oculta bloques del DOM según condiciones lógicas.</p>
        </div>
        <div class="directive-item">
          <code>v-show</code>
          <p>Alterna la visibilidad con CSS (el elemento permanece en el DOM).</p>
        </div>
        <div class="directive-item">
          <code>@click / @keyup.enter</code>
          <p>Escucha eventos del usuario para ejecutar métodos.</p>
        </div>
        <div class="directive-item">
          <code>:key</code>
          <p>Identificador único para cada ítem en un <code>v-for</code>.</p>
        </div>
      </div>
    </section>

  </div>
</template>

<style scoped>
.tareas-page {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

/* Card */
.card {
  background: var(--color-surface);
  border: 1px solid var(--border-color);
  border-radius: 8px;
  padding: 1.5rem;
}

.card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 1.2rem;
}

.card-header h2 {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
}

.badge {
  background-color: var(--color-primary);
  color: white;
  font-size: 0.78rem;
  font-weight: 600;
  padding: 0.25rem 0.6rem;
  border-radius: 999px;
}

/* Inputs row */
.input-row {
  display: flex;
  gap: 0.6rem;
  margin-bottom: 1rem;
  flex-wrap: wrap;
}

.text-input {
  flex: 1;
  min-width: 160px;
  padding: 0.55rem 0.85rem;
  border: 1px solid var(--border-color);
  border-radius: 6px;
  font-size: 0.95rem;
  font-family: var(--font-sans);
  background: var(--color-bg);
  color: var(--text-primary);
  transition: border-color 0.2s;
}

.text-input:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgba(30, 126, 52, 0.12);
}

/* Buttons */
.btn {
  padding: 0.55rem 1rem;
  border: none;
  border-radius: 6px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.2s, transform 0.1s;
  white-space: nowrap;
}

.btn:active {
  transform: scale(0.97);
}

.btn-primary {
  background-color: var(--color-primary);
  color: white;
}

.btn-primary:hover {
  background-color: var(--color-primary-hover);
}

.btn-secondary {
  background-color: #495057;
  color: white;
}

.btn-secondary:hover {
  background-color: #343a40;
}

.btn-danger {
  background-color: #e53935;
  color: white;
}

.btn-danger:hover {
  background-color: #b71c1c;
}

.btn-sm {
  padding: 0.35rem 0.7rem;
  font-size: 0.82rem;
}

/* Task list */
.task-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.task-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.7rem 1rem;
  background: var(--color-bg);
  border: 1px solid var(--border-color);
  border-radius: 6px;
  transition: box-shadow 0.15s;
}

.task-item:hover {
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.07);
}

.task-index {
  font-weight: 700;
  color: var(--color-primary);
  min-width: 1.5rem;
}

.task-text {
  flex: 1;
  font-size: 0.95rem;
  color: var(--text-primary);
}

/* Messages */
.empty-msg {
  text-align: center;
  color: var(--text-secondary);
  font-size: 0.95rem;
  padding: 1.5rem;
  border: 2px dashed var(--border-color);
  border-radius: 6px;
  margin-top: 0.5rem;
}

.hidden-msg {
  text-align: center;
  color: var(--text-secondary);
  font-size: 0.95rem;
  font-style: italic;
  padding: 1rem;
  background: var(--color-bg);
  border-radius: 6px;
  margin-top: 0.5rem;
}

/* Info card */
.info-card {
  background: #f0f7f1;
  border-color: rgba(30, 126, 52, 0.2);
}

.info-card h2 {
  font-size: 1.1rem;
  color: var(--color-primary);
  margin-bottom: 1rem;
}

.directives-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1rem;
}

.directive-item {
  background: white;
  border: 1px solid rgba(30, 126, 52, 0.15);
  border-radius: 6px;
  padding: 0.9rem 1rem;
}

.directive-item code {
  display: block;
  font-size: 0.85rem;
  font-weight: 700;
  color: var(--color-primary);
  margin-bottom: 0.4rem;
  font-family: 'Courier New', monospace;
}

.directive-item p {
  font-size: 0.82rem;
  color: var(--text-secondary);
  line-height: 1.4;
}

@media (max-width: 600px) {
  .input-row {
    flex-direction: column;
  }

  .btn {
    width: 100%;
  }
}
</style>
