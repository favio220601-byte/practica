<template>
  <form @submit.prevent="registrar">
    <input v-model="empresa" type="text" placeholder="Empresa" />
    <input v-model="contacto" type="text" placeholder="Contacto" />
    <input v-model="telefono" type="text" placeholder="Teléfono" />
    <input v-model="correo" type="email" placeholder="Correo" />

    <select v-model="categoria">
      <option value="">Seleccione categoría</option>
      <option>Alimentos</option>
      <option>Tecnología</option>
      <option>Ropa</option>
      <option>Servicios</option>
      <option>Otros</option>
    </select>

    <input v-model="ciudad" type="text" placeholder="Ciudad" />

    <button type="submit">Registrar proveedor</button>

    <p>{{ mensaje }}</p>

    <div v-if="proveedores.length > 0">
      <table border="1">
        <tr>
          <th>Empresa</th>
          <th>Contacto</th>
          <th>Teléfono</th>
          <th>Correo</th>
          <th>Categoría</th>
          <th>Ciudad</th>
        </tr>

        <tr v-for="(p, index) in proveedores" :key="index">
          <td>{{ p.empresa }}</td>
          <td>{{ p.contacto }}</td>
          <td>{{ p.telefono }}</td>
          <td>{{ p.correo }}</td>
          <td>{{ p.categoria }}</td>
          <td>{{ p.ciudad }}</td>
        </tr>
      </table>
    </div>

    <p v-else>No existen proveedores registrados.</p>
  </form>
</template>

<script setup>
import { ref } from "vue";

const empresa = ref("");
const contacto = ref("");
const telefono = ref("");
const correo = ref("");
const categoria = ref("");
const ciudad = ref("");

const mensaje = ref("");
const proveedores = ref([]);

function registrar() {
  if (
    empresa.value === "" ||
    contacto.value === "" ||
    telefono.value === "" ||
    correo.value === "" ||
    categoria.value === ""
  ) {
    mensaje.value = "Complete todos los campos obligatorios.";
    return;
  }

  proveedores.value.push({
    empresa: empresa.value,
    contacto: contacto.value,
    telefono: telefono.value,
    correo: correo.value,
    categoria: categoria.value,
    ciudad: ciudad.value,
  });

  mensaje.value = "Proveedor registrado correctamente.";

  empresa.value = "";
  contacto.value = "";
  telefono.value = "";
  correo.value = "";
  categoria.value = "";
  ciudad.value = "";
}
</script>

<style scoped>
input,
select,
button {
  display: block;
  margin: 8px 0;
  padding: 8px;
}

table {
  margin-top: 20px;
  width: 100%;
  border-collapse: collapse;
}

th,
td {
  padding: 8px;
}
</style>