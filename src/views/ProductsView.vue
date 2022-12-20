<template>
    <div class="container">
        <div class="row">
            <h1 class="display-1">Products</h1>
            <table>
    <tr>
      <th>ID</th>
      <th>Image</th>
      <th>Make</th>
      <th>Spec</th>
      <th>Amount</th>
    </tr>
    <tr v-for="item in products" :key="item">
      <td>{{ item.id }}</td>
      <td><img :src="item.image" class="card-img-top"></td>
      <td>{{ item.make }}</td>
      <td>{{ item.spec }}</td>
      <td>{{ item.amount }}</td>
    </tr>
  </table>
        </div>
    </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters(["products"]),
  },
  methods: {
    ...mapActions(["fetchAllProducts"]),
  },
  created() {
    this.fetchAllProducts();
  },
}
</script>

<style scoped>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
  max-width: 600px;
}

td,
th {
  border: 1px solid #333;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>