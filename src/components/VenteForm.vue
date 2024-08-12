<template>
  <div class="vente-form">
    <h2>Ajouter une Vente</h2>
    <form @submit.prevent="submitForm">
      <div class="mb-3">
        <label for="produit">Produit :</label>
        <input id="produit" v-model="produit" type="text" class="form-control" required />
      </div>
      <div class="mb-3">
        <label for="montant">Montant :</label>
        <input id="montant" v-model.number="montant" type="number" class="form-control" required />
      </div>
      <button type="submit" class="btn btn-primary">Enregistrer</button>
    </form>
  </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue';

const produit = ref('');
const montant = ref(0);
const emit = defineEmits(['vente-enregistree']);

const submitForm = () => {
  const vente = { produit: produit.value, montant: montant.value };
  emit('vente-enregistree', vente);
  produit.value = '';
  montant.value = 0;
};
</script>

<style scoped>
.vente-form {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.btn-primary {
  background-color: #4682b4;
  border-color: #4682b4;
  color: #ffffff;
}

.btn-primary:hover {
  background-color: #4169e1;
  border-color: #4169e1;
}
</style>
