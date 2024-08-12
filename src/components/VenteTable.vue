<template>
  <div>
    <h2>Liste des Ventes</h2>
    <table class="table">
      <thead>
        <tr>
          <th>Produit</th>
          <th>Montant</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(vente, index) in ventes" :key="index">
          <td>{{ vente.produit }}</td>
          <td>{{ vente.montant }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  ventes: {
    type: Array,
    required: true
  }
});
</script>

<style scoped>
.table {
  width: 100%;
  margin-top: 20px;
  border-collapse: collapse;
}

.table thead {
  background-color: #4682b4;
  color: #ffffff;
}

.table th, .table td {
  padding: 10px;
  border: 1px solid #dddddd;
}
</style>
