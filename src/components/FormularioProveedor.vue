<script setup>
import { ref } from 'vue'

const emit = defineEmits(['registrar'])

const empresa = ref('')
const contacto = ref('')
const telefono = ref('')
const correo = ref('')
const categoria = ref('')
const ciudad = ref('')

const mensaje = ref('')
const tipoMensaje = ref('')

const categorias = ['Alimentos', 'Tecnología', 'Ropa', 'Servicios', 'Otros']

function registrar() {
  if (!empresa.value || !contacto.value || !telefono.value || !correo.value || !categoria.value) {
    mensaje.value = 'Complete todos los campos obligatorios.'
    tipoMensaje.value = 'error'
    return
  }

  emit('registrar', {
    empresa: empresa.value,
    contacto: contacto.value,
    telefono: telefono.value,
    correo: correo.value,
    categoria: categoria.value,
    ciudad: ciudad.value
  })

  mensaje.value = 'Proveedor registrado correctamente.'
  tipoMensaje.value = 'exito'

  empresa.value = ''
  contacto.value = ''
  telefono.value = ''
  correo.value = ''
  categoria.value = ''
  ciudad.value = ''
}
</script>

<template>
  <div class="formulario-container">
    <h2>Registrar Proveedor</h2>

    <div v-if="mensaje" :class="['mensaje', tipoMensaje]">
      {{ mensaje }}
    </div>

    <form @submit.prevent="registrar">
      <div class="campo">
        <label for="empresa">Nombre de la empresa *</label>
        <input id="empresa" v-model="empresa" type="text" placeholder="Ingrese el nombre de la empresa" />
      </div>

      <div class="campo">
        <label for="contacto">Nombre del contacto *</label>
        <input id="contacto" v-model="contacto" type="text" placeholder="Ingrese el nombre del contacto" />
      </div>

      <div class="campo">
        <label for="telefono">Teléfono *</label>
        <input id="telefono" v-model="telefono" type="text" placeholder="Ingrese el teléfono" />
      </div>

      <div class="campo">
        <label for="correo">Correo electrónico *</label>
        <input id="correo" v-model="correo" type="email" placeholder="Ingrese el correo electrónico" />
      </div>

      <div class="campo">
        <label for="categoria">Categoría *</label>
        <select id="categoria" v-model="categoria">
          <option value="" disabled>Seleccione una categoría</option>
          <option v-for="cat in categorias" :key="cat" :value="cat">{{ cat }}</option>
        </select>
      </div>

      <div class="campo">
        <label for="ciudad">Ciudad</label>
        <input id="ciudad" v-model="ciudad" type="text" placeholder="Ingrese la ciudad" />
      </div>

      <button type="submit" class="btn-registrar">Registrar proveedor</button>
    </form>
  </div>
</template>

<style scoped>
.formulario-container {
  background: white;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  padding: 1.5rem 2rem;
  max-width: 700px;
  margin: 0 auto 2rem auto;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.formulario-container h2 {
  margin-top: 0;
  margin-bottom: 1rem;
  color: #1a237e;
  font-size: 1.3rem;
}

.campo {
  margin-bottom: 1rem;
}

.campo label {
  display: block;
  margin-bottom: 0.3rem;
  font-weight: 600;
  font-size: 0.9rem;
  color: #333;
}

.campo input,
.campo select {
  width: 100%;
  padding: 0.6rem 0.8rem;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 0.95rem;
  box-sizing: border-box;
}

.campo input:focus,
.campo select:focus {
  outline: none;
  border-color: #1a237e;
  box-shadow: 0 0 0 2px rgba(26, 35, 126, 0.2);
}

.btn-registrar {
  width: 100%;
  padding: 0.75rem;
  background-color: #1a237e;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  margin-top: 0.5rem;
}

.btn-registrar:hover {
  background-color: #283593;
}

.mensaje {
  padding: 0.7rem 1rem;
  border-radius: 6px;
  margin-bottom: 1rem;
  font-weight: 500;
}

.mensaje.error {
  background-color: #ffebee;
  color: #c62828;
  border: 1px solid #ef9a9a;
}

.mensaje.exito {
  background-color: #e8f5e9;
  color: #2e7d32;
  border: 1px solid #a5d6a7;
}
</style>
