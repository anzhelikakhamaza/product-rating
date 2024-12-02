<script setup>
  import { ref } from 'vue';

  import RatingStars from "@/components/RatingStars.vue";
  import RatingDisplay from "@/components/RatingDisplay.vue";
</script>

<template>
  <div>
    <h1>Product Rating</h1>
    <RatingStars />
    <RatingDisplay />
  </div>
</template>

<style scoped>

</style>
