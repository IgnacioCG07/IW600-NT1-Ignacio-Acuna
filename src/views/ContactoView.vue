<template>
  <div class="contacto-container">
    <h1>Contacto - Mercado Ñuble Digital</h1>
    <p>Escríbenos si tienes dudas o si eres productor y quieres sumarte a la plataforma.</p>

    <!-- Formulario (se muestra si aún no ha sido enviado con éxito) -->
    <form v-if="!enviado" @submit.prevent="procesarFormulario" class="formulario">
      
      <!-- Mensaje de error si falla la validación -->
      <div v-if="mensajeError" class="mensaje-error">
        {{ mensajeError }}
      </div>

      <div class="campo">
        <label for="nombre">Nombre completo *</label>
        <input 
          id="nombre" 
          type="text" 
          v-model.trim="form.nombre" 
          placeholder="Ej: María Pérez" 
        />
      </div>

      <div class="campo">
        <label for="email">Correo electrónico *</label>
        <input 
          id="email" 
          type="email" 
          v-model.trim="form.email" 
          placeholder="ejemplo@correo.com" 
        />
      </div>

      <div class="campo">
        <label for="telefono">Teléfono *</label>
        <input 
          id="telefono" 
          type="tel" 
          v-model.trim="form.telefono" 
          placeholder="+56 9 1234 5678" 
        />
      </div>

      <div class="campo">
        <label for="comuna">Comuna *</label>
        <select id="comuna" v-model="form.comuna">
          <option value="">Selecciona tu comuna</option>
          <option value="Chillán">Chillán</option>
          <option value="San Carlos">San Carlos</option>
          <option value="Quirihue">Quirihue</option>
          <option value="Coihueco">Coihueco</option>
          <option value="El Carmen">El Carmen</option>
          <option value="Otra">Otra comuna de Ñuble</option>
        </select>
      </div>

      <div class="campo">
        <label for="mensaje">Mensaje *</label>
        <textarea 
          id="mensaje" 
          v-model.trim="form.mensaje" 
          rows="4" 
          placeholder="Escribe tu mensaje aquí..."
        ></textarea>
      </div>

      <button type="submit" class="btn-enviar">Enviar mensaje</button>
    </form>

    <!-- Resumen y confirmación tras validación exitosa -->
    <div v-else class="resumen-confirmacion">
      <h2>¡Mensaje recibido con éxito!</h2>
      <p>Gracias por contactarte con Mercado Ñuble Digital. A continuación te mostramos el resumen de tus datos:</p>
      
      <div class="datos-resumen">
        <p><strong>Nombre:</strong> {{ form.nombre }}</p>
        <p><strong>Correo:</strong> {{ form.email }}</p>
        <p><strong>Teléfono:</strong> {{ form.telefono }}</p>
        <p><strong>Comuna:</strong> {{ form.comuna }}</p>
        <p><strong>Mensaje:</strong> {{ form.mensaje }}</p>
      </div>

      <button @click="reiniciarFormulario" class="btn-nuevo">Enviar otro mensaje</button>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const form = reactive({
  nombre: '',
  email: '',
  telefono: '',
  comuna: '',
  mensaje: ''
})

const mensajeError = ref('')
const enviado = ref(false)

const procesarFormulario = () => {
  // Validamos que ningún campo esté vacío
  if (!form.nombre || !form.email || !form.telefono || !form.comuna || !form.mensaje) {
    mensajeError.value = 'Por favor, completa todos los campos del formulario.'
    return
  }

  // Validación básica de correo electrónico
  if (!form.email.includes('@')) {
    mensajeError.value = 'Ingresa un correo electrónico válido.'
    return
  }

  // Si supera la validación
  mensajeError.value = ''
  enviado.value = true
}

const reiniciarFormulario = () => {
  form.nombre = ''
  form.email = ''
  form.telefono = ''
  form.comuna = ''
  form.mensaje = ''
  enviado.value = false
}
</script>

<style scoped>
.contacto-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.formulario {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
  margin-top: 1.5rem;
  background: #ffffff;
  padding: 1.5rem;
  border-radius: 8px;
  border: 1px solid #e0e0e0;
}

.campo {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}

.campo label {
  font-weight: bold;
  font-size: 0.95rem;
}

.campo input,
.campo select,
.campo textarea {
  padding: 0.6rem;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 1rem;
}

.mensaje-error {
  background-color: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
  padding: 0.8rem;
  border-radius: 6px;
}

.btn-enviar {
  padding: 0.8rem;
  background-color: #2e7d32;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
}

.btn-enviar:hover {
  background-color: #1b5e20;
}

.resumen-confirmacion {
  margin-top: 1.5rem;
  background-color: #e8f5e9;
  border: 1px solid #c8e6c9;
  padding: 1.5rem;
  border-radius: 8px;
}

.datos-resumen {
  margin: 1rem 0;
  line-height: 1.6;
}

.btn-nuevo {
  padding: 0.6rem 1rem;
  background-color: #555;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
</style>