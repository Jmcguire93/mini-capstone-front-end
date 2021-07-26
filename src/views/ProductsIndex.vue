<template>
  <div class="products-index">
    <h1>{{ message }}</h1>

    <div v-for="post in products" :key="post.id">
      <h2>Title: {{ post.title }}</h2>
      <p>Body: {{ post.body }}</p>
      <img v-bind:src="post.image" alt="post.title" />
      <!-- <p><router-link to="`/show/${post.id}`">Link to this post</router-link></p> -->
      <p><router-link v-bind:to="`/products/${post.id}`">Link to post</router-link></p>
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
