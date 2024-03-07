<template>
  <div >
    <h1 class="display-5 text-center">Examen DWEC: Diego Valés Sierra</h1>
    <div class="form-outline mx-2" data-mdb-input-init>
      <input @keydown.enter="buscarUser"  v-model="usuario" type="search" id="form1" class="form-control" placeholder="Introduce usuario" aria-label="Search" />
      <div class="alert alert-danger" v-if="encontrado === false" role="alert">
      Usuario no encontrado
      </div>
    </div>
    <div v-if="encontrado===true" class="row">
      <SuscripcionGitHub v-for="sus in suscripciones" :key="sus.full_name" :="sus" class="col-3"></SuscripcionGitHub>
    </div>
    
    
    {{ usuario }}
  </div>
</template>


<script setup>
import { ref } from 'vue';
import SuscripcionGitHub from './components/SuscripcionGitHub.vue';


let usuario = ref('');
let suscripciones = ref([]);
let encontrado = ref(true);


async function buscarUser () {
  const URL = "https://api.github.com/users/" + usuario.value + "/subscriptions";

  const res = await fetch(URL);

  if (!res.ok) {
    encontrado.value = false
  } else {
    encontrado.value = true
    suscripciones.value = await res.json();
  }
}


</script>

<style>

</style>./components/SuscripcionGitHub.vue
