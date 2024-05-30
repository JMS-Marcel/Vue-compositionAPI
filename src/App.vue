<script setup>
//Forms
import { ref } from 'vue';
import ProductDisplay from './components/ProductDisplay.vue';
import ReviewForm from './components/ReviewForm.vue'
import ReviewList from './components/ReviewList.vue'


  let cart = ref([]);
  let reviews = ref([]);
  let premium = true;
  function updateCart(id) {
    cart.value.push(id);
  }
  function addReview(review){
    reviews.value.push(review)
  }
</script>

<template>
  <nav class="nav-bar"></nav>
  <div class="cart">Cart({{ cart.length }})</div>
  <ProductDisplay :premium="premium" @add-to-cart="updateCart"/>
  <ReviewList :reviews="reviews"/>
  <ReviewForm @review-submitted="addReview" />
</template>

<style scoped>

</style>
