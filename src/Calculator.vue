<script setup>
import Buttons from "./components/Buttons.vue";
</script>

<template>
  <div>
    <header>
      <div class="wrapper">
        <Buttons />
      </div>
    </header>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}
</style>
