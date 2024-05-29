<script setup lang="ts">
  import { computed, ref } from 'vue';

  const props = defineProps<{
    premium: {
      type: boolean,
      required: true
    }
  }>();

  console.log(props.premium);
  
  const product = ref('Socks');
  const brand = ref('Vue Mastery');

  
  let selectedVariant = ref(0);

  const details = ['50% cotton', '30% wool', '20% polyester'];
  const variants = [
    {id: 2234, color: 'green',image:'../public/images/socks_green.jpg', quantity:50},
    {id: 2235, color: 'blue',image:'../public/images/socks_blue.jpg', quantity:0},
  ];


  function updateVariant(index){
    selectedVariant.value = index;
  }

  const title = computed(()=>{
    return brand.value + ' ' + product.value;
  });
  const image = computed(()=>{
    return variants[selectedVariant.value].image
  })
  const inStock = computed(()=>{
    return variants[selectedVariant.value].quantity;
  })
  const shipping = computed(()=>{

   if(props.premium){
    return 'Free';
   } 
    return 2.99;
  })
</script>

<template >
    <div class="product-display">
      <div class="product-container">
        <div class="product-image">
          <img :src="image">
        </div>
        <div class="product-info">
          <h1>{{ title }}</h1>
          
          <p v-if="inStock">In Stock</p> 
          <p v-else >Out of Stock</p> 

          <p>Shipping: {{ shipping }}</p>
          <ul>
            <li v-for="detail in details">{{ detail }}</li>
          </ul>

          <div 
            v-for="variant, index in variants"
            :key="variant.id"
            @mouseover="updateVariant(index)"
            class="color-circle"
            :style="{ backgroundColor:variant.color }">
          </div>

          <button 
            class="button"
            :class="{disabledButton: !inStock}"
            :disabled="!inStock"
            @click="$emit('add-to-cart', variants[selectedVariant].id)">
            Add to Cart
          </button>

        </div>
      </div>
  </div>
</template>