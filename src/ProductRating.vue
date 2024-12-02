<script setup>
  import { ref } from 'vue';

  import RatingStars from "@/components/RatingStars.vue";
  import RatingDisplay from "@/components/RatingDisplay.vue";

  const ratings = ref([]);
  let average = ref(0);

  const updateRating = (newRating) => {
    ratings.value.push(newRating);
    average.value = ratings.value.reduce((acc, rating) => acc + rating, 0) / ratings.value.length;
  }

</script>

<template>
  <div>
    <h1>Product Rating</h1>
    <RatingStars @ratingData = "updateRating"/>
    <RatingDisplay :average="average"/>
  </div>
</template>

<style scoped>

</style>
