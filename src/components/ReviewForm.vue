<script setup>
  let name = '';
  let review = '';
  let rating = null;

  function onSubmit(){
    let productReview = {
      name:name.value,
      review: review.value,
      rating:rating.value
    }
  
    name.value = '';
    review.value = '';
    rating.value = null;
  }
</script>
<template>

  <form class="review-form" @submit.prevent="onSubmit, $emit('review-submitted', productReview)">
    <h3>Leave a review</h3>
    <label for="name">Name:</label>
    <input type="text" id="name" v-model="name">

    <label for="review">Review</label>
    <textarea id="review" v-model="review"></textarea>

    <label for="rating" >Rating:</label>
    <select id="rating"v-model.number="rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>

    <input class="button" type="submit" value="Submit">
  </form>


</template>