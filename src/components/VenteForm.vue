<template>
  <div class="card p-4">
    <h3 class="card-title mb-4">Enregistrer une vente</h3>
    <form @submit.prevent="submitForm">
      <div class="mb-3">
        <label for="productName" class="form-label">Nom du produit :</label>
        <input id="productName" v-model="productName" type="text" class="form-control" />
      </div>
      <div class="mb-3">
        <label for="quantity" class="form-label">Quantité :</label>
        <input id="quantity" v-model.number="quantity" type="number" class="form-control" min="1" />
      </div>
      <div class="mb-3">
        <label for="price" class="form-label">Prix unitaire :</label>
        <input id="price" v-model.number="price" type="number" class="form-control" min="0" step="0.01" />
      </div>
      <div class="mb-3">
        <label for="total" class="form-label">Total :</label>
        <input id="total" :value="total" type="text" class="form-control" readonly />
      </div>
      <button type="submit" class="btn btn-primary">Enregistrer</button>
    </form>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const productName = ref('');
const quantity = ref(1);
const price = ref(0);

const total = computed(() => {
  return (quantity.value * price.value).toFixed(2);
});

const submitForm = () => {
  if (!productName.value || quantity.value <= 0 || price.value <= 0) {
    alert('Veuillez remplir tous les champs correctement.');
    return;
  }
  const vente = {
    productName: productName.value,
    quantity: quantity.value,
    price: price.value,
    total: total.value,
  };
  emit('vente-enregistree', vente);
  productName.value = '';
  quantity.value = 1;
  price.value = 0;
};
</script>

<style scoped>
.card {
  background: rgba(255, 255, 255, 0.9);
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}
</style>
