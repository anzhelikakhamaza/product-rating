<script setup>
import { ref } from 'vue';


const activeStar = ref(0);

const rate = (rating) => {
  activeStar.value = rating;
  this.$emit('ratingData', rating);
};
</script>

<template>
  <div class="card">
    <span
        v-for="n in 5"
        @click="rate(n)"
        class="star"
        :class="{ one: n === 1 && activeStar >= n,
                two: n === 2 && activeStar >= n,
                three: n === 3 && activeStar >= n,
                four: n === 4 && activeStar >= n,
                five: n === 5 && activeStar >= n }"
    >
      ★
    </span>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  min-height: 50vh;
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: center;
  background: hsl(137, 46%, 24%);
  font-family: "Poppins", sans-serif;
}

.card {
  max-width: 33rem;
  background: #fff;
  margin: 0 1rem;
  padding: 1rem;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
  width: 100%;
  border-radius: 0.5rem;
}

.star {
  font-size: 10vh;
  cursor: pointer;
}

.one {
  color: rgb(255, 0, 0);
}

.two {
  color: rgb(255, 106, 0);
}

.three {
  color: rgb(251, 255, 120);
}

.four {
  color: rgb(255, 255, 0);
}

.five {
  color: rgb(24, 159, 14);
}
</style>