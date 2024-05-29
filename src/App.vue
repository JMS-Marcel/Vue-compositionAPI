<script setup>

import { ref } from 'vue';
import ProductDisplay from './components/ProductDisplay.vue';


  let cart = ref([]);
  let premium = true;
  function updateCart(id) {
    cart.value.push(id);
  }
</script>

<template>
  <nav class="nav-bar"></nav>
  <div class="cart">Cart({{ cart.length }})</div>
  <ProductDisplay :premium="premium" @add-to-cart="updateCart"/>
</template>

<style scoped>

</style>
