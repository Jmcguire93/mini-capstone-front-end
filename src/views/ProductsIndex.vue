<template>
  <div class="products-index">
    <h1>{{ message }}</h1>

    <div v-for="product in products" :key="product.id">
      <h2>Name: {{ product.name }}</h2>
      <p>Description: {{ product.desscription }}</p>
      <img v-bind:src="product.image" alt="product.name" />

      <p><router-link v-bind:to="`/products/${product.id}`">Link to product</router-link></p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Products",
      products: [],
      newPostParams: {},
      currentPost: {},
    };
  },
  created: function () {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      axios.get("http://localhost:3000/products").then((response) => {
        this.products = response.data;
        console.log("All products:", this.products);
      });
    },
  },
};
</script>
