<template>
  <EncabezadoApp
    titulo="Registro de Proveedores"
    subtitulo="Sistema de apoyo para la gestión comercial"
  />

  <FormularioProveedor />
</template>

<script setup>
import EncabezadoApp from "./components/Encabezado.vue";
import FormularioProveedor from "./components/form.vue";
</script>

<style>
body {
  font-family: Arial, sans-serif;
  margin: 20px;
}
</style>