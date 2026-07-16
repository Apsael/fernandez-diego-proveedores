<script setup>
const props = defineProps({
  titulo: String,
  subtitulo: String
})
</script>

<template>
  <header class="encabezado">
    <h1>{{ titulo }}</h1>
    <p>{{ subtitulo }}</p>
  </header>
</template>

<style scoped>
.encabezado {
  background-color: #1a237e;
  color: white;
  padding: 1.5rem 2rem;
  text-align: center;
  border-radius: 0 0 12px 12px;
  margin-bottom: 2rem;
}

.encabezado h1 {
  margin: 0 0 0.5rem 0;
  font-size: 1.8rem;
  letter-spacing: 1px;
}

.encabezado p {
  margin: 0;
  font-size: 1rem;
  opacity: 0.85;
}
</style>
