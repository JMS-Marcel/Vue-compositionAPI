<script setup>
import { ref } from 'vue';
import ProductDisplay from './components/ProductDisplay.vue';


  let cart = ref(0);
  let premium = true;
</script>

<template>
  <nav class="nav-bar"></nav>
  <div class="cart">Cart({{ cart }})</div>
  <ProductDisplay :premium="premium"/>
</template>

<style scoped>

</style>
