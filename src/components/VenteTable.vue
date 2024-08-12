<template>
  <div class="card p-4">
    <h3 class="card-title mb-4">Liste des ventes</h3>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>Nom du produit</th>
          <th>Quantité</th>
          <th>Prix unitaire</th>
          <th>Total</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(vente, index) in ventes" :key="index">
          <td>{{ vente.productName }}</td>
          <td>{{ vente.quantity }}</td>
          <td>{{ vente.price.toFixed(2) }}</td>
          <td>{{ vente.total }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const props = defineProps({
  ventes: Array
});
</script>

<style scoped>
.card {
  background: rgba(255, 255, 255, 0.9);
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}
.table {
  margin-bottom: 0;
}
</style>
