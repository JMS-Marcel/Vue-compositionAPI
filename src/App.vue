<script setup>
import { onMounted, ref } from 'vue';



  const product = ref('Socks');
  let cart = ref(0);
  let image = ref('../public/images/socks_blue.jpg');
  const inStock = ref(false);
  const details = ['50% cotton', '30% wool', '20% polyester'];
  const variants = [
    {id: 2234, color: 'green',image:'../public/images/socks_green.jpg'},
    {id: 2235, color: 'blue',image:'../public/images/socks_blue.jpg'},
  ];

  function addToCart(){
    cart.value ++;
  }
  function updateImage(variantImage){
    image.value = variantImage;
  }
  
  
  

</script>

<template>
  <nav class="nav-bar"></nav>
  <div class="cart">Cart({{ cart }})</div>
    <div class="product-display">
      <div class="product-container">
        <div class="product-image">
          <img :src="image">
        </div>
        <div class="product-info">
          <h1>{{ product }}</h1>
          <p v-if="inStock">In Stock</p> 
          <p v-else >Out of Stock</p> 
          <ul>
            <li v-for="detail in details">{{ detail }}</li>
          </ul>

          <div 
            v-for="variant in variants" 
            :key="variant.id"
            @mouseover="updateImage(variant.image)"
            class="color-circle"
            :style="{ backgroundColor:variant.color }">
          </div>

          <button 
            class="button"
            :class="{disabledButton: !inStock}"
            :disabled="!inStock"
            @click="addToCart">
            Add to Cart
          </button>

        </div>
      </div>
  </div>
</template>

<style scoped>

</style>
