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
  background: linear-gradient(135deg, rgba(255, 0, 150, 0.8), rgba(0, 204, 255, 0.8));
  min-height: 100vh;
  color: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(255, 0, 150, 0.5);
}

.header {
  text-align: center;
  margin-bottom: 30px;
}

.header h1 {
  font-family: 'Arial', sans-serif;
  font-size: 2.5rem;
  background: linear-gradient(90deg, #ff007f, #00d4ff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient 3s infinite;
}

@keyframes gradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
</style>
