<script setup>
  
  const props = defineProps({
    reviews: {
      type: Array,
      required: true
    }
  });
  console.log(props.reviews);
  
</script>
<template>
  <div v-if="reviews.length" class="review-container">
    <h3>Reviews:</h3>
    <ul>
      
      <li v-for="review, index in reviews" :key="index">
        <strong>{{ review.name }}</strong> a donné <strong>{{ review.rating }} étoile(s).</strong>✨
        <br>
        <br>
        <strong>"{{ review.review }}"</strong>⌛
      </li>
    </ul>
  </div>
</template>