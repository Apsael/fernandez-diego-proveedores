<script setup>
import { ref } from 'vue'
import EncabezadoApp from './components/EncabezadoApp.vue'
import FormularioProveedor from './components/FormularioProveedor.vue'

const proveedores = ref([])

function agregarProveedor(proveedor) {
  proveedores.value.push(proveedor)
}
</script>

<template>
  <div id="app-container">
    <EncabezadoApp
      titulo="Registro de Proveedores"
      subtitulo="Sistema de apoyo para la gestión comercial"
    />

    <FormularioProveedor @registrar="agregarProveedor" />

    <div class="listado-container">
      <h2>Listado de Proveedores</h2>

      <div v-if="proveedores.length === 0" class="sin-datos">
        No existen proveedores registrados.
      </div>

      <div v-else class="tabla-container">
        <table>
          <thead>
            <tr>
              <th>Empresa</th>
              <th>Contacto</th>
              <th>Teléfono</th>
              <th>Correo</th>
              <th>Categoría</th>
              <th>Ciudad</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(proveedor, index) in proveedores" :key="index">
              <td>{{ proveedor.empresa }}</td>
              <td>{{ proveedor.contacto }}</td>
              <td>{{ proveedor.telefono }}</td>
              <td>{{ proveedor.correo }}</td>
              <td>{{ proveedor.categoria }}</td>
              <td>{{ proveedor.ciudad }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f5f5f5;
  color: #333;
}

#app-container {
  max-width: 900px;
  margin: 0 auto;
  padding: 0 1rem 2rem 1rem;
}

.listado-container {
  max-width: 700px;
  margin: 0 auto;
}

.listado-container h2 {
  margin-bottom: 1rem;
  color: #1a237e;
  font-size: 1.3rem;
}

.sin-datos {
  text-align: center;
  padding: 2rem;
  background: white;
  border: 1px dashed #ccc;
  border-radius: 12px;
  color: #777;
  font-size: 1rem;
}

.tabla-container {
  overflow-x: auto;
  background: white;
  border-radius: 12px;
  border: 1px solid #e0e0e0;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.9rem;
}

thead {
  background-color: #1a237e;
  color: white;
}

th,
td {
  padding: 0.7rem 1rem;
  text-align: left;
  border-bottom: 1px solid #eee;
}

tbody tr:hover {
  background-color: #f5f5f5;
}

tbody tr:last-child td {
  border-bottom: none;
}
</style>
