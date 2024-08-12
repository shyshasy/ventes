<template>
  <div id="app" class="container mt-5">
    <div class="header">
      <h1>Enregistrement des Ventes</h1>
    </div>
    <VenteForm @vente-enregistree="ajouterVente" />
    <VenteTable :ventes="ventes" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import VenteForm from './components/VenteForm.vue';
import VenteTable from './components/VenteTable.vue';

const ventes = ref([]);

const ajouterVente = (vente) => {
  ventes.value.push(vente);
};
</script>

<style>
#app {
  background: linear-gradient(135deg, rgba(200, 0, 120, 0.7), rgba(0, 204, 255, 0.8));
  min-height: 100vh;
  color: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(200, 0, 120, 0.4);
}

.header {
  text-align: center;
  margin-bottom: 30px;
}

.header h1 {
  font-family: 'Arial', sans-serif;
  font-size: 2.5rem;
  font-weight: bold;
  color: #fff;
  text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.7);
  background: rgba(0, 0, 0, 0.2);
  padding: 10px 20px;
  border-radius: 10px;
}
</style>
